# Julia SSA-form IR

Julia, statik tekil atama ara temsilini ([SSA IR](https://en.wikipedia.org/wiki/Static_single-assignment_form)) optimizasyon yapmak için kullanır. Bu IR, LLVM IR'den farklıdır ve Julia'ya özgüdür. Julia'ya özgü optimizasyonlara olanak tanır.

1. Temel bloklar (kontrol akışı olmayan bölgeler) açıkça anotlanmıştır.
2. if/else ve döngüler `goto` ifadelerine dönüştürülür.
3. birden fazla işlemi içeren satırlar, değişkenler tanımlanarak birden fazla satıra bölünür.

Örnek olarak aşağıdaki Julia kodu:

```julia
function foo(x)
    y = sin(x)
    if x > 5.0
        y = y + cos(x)
    end
    return exp(2) + y
end
```

`Float64` argümanı ile çağrıldığında şuna çevrilir:

```julia
using InteractiveUtils
@code_typed foo(1.0)
```

```llvm
CodeInfo(
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
2 ─ %4 = invoke Main.cos(x::Float64)::Float64
└── %5 = Base.add_float(%1, %4)::Float64
3 ┄ %6 = φ (#2 => %5, #1 => %1)::Float64
│   %7 = Base.add_float(7.38905609893065, %6)::Float64
└──      return %7
) => Float64
```

Bu örnekte, bu değişikliklerin hepsini görebiliriz.

1. İlk temel blok, her şeydir

```llvm
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
```

2. `if` ifadesi, `x>5` koşulu sağlanmadığında 3. temel bloğa giden `goto #3 if not %2` olarak çevrilir ve aksi takdirde ikinci temel bloğa gider.
3. `%2` bir SSA değeri olup `x > 5` ifadesini temsil etmek için tanıtılmıştır.

## Background

Julia 0.7'den itibaren, derleyicinin bazı bölümleri yeni bir [SSA-form](https://en.wikipedia.org/wiki/Static_single_assignment_form) ara temsil (IR) kullanmaktadır. Tarihsel olarak, derleyici, Julia AST'sinin düşürülmüş bir biçiminden doğrudan LLVM IR üretirdi. Bu biçim, çoğu sözdizimsel soyutlamanın kaldırıldığı, ancak yine de soyut bir sözdizim ağacına çok benzeyen bir görünümdeydi. Zamanla, optimizasyonları kolaylaştırmak amacıyla, bu IR'ye SSA değerleri eklendi ve IR lineer hale getirildi (yani, fonksiyon argümanlarının yalnızca SSA değerleri veya sabitler olabileceği bir biçime dönüştürüldü). Ancak, IR'de Phi düğümlerinin eksikliği nedeniyle, IR'de non-SSA değerler (slotlar) kalmaya devam etti (geri kenarlar ve koşullu kontrol akışının yeniden birleştirilmesi için gerekli). Bu durum, orta uç optimizasyonları gerçekleştirirken SSA form temsilinin faydasını büyük ölçüde azalttı. Tam bir SSA form temsili olmadan bu optimizasyonların çalışmasını sağlamak için bazı kahramanca çabalar sarf edildi, ancak böyle bir temsilin eksikliği nihayetinde engelleyici bir unsur olarak ortaya çıktı.

## Categories of IR nodes

SSA IR temsili dört kategori IR düğümü içerir: Phi, Pi, PhiC ve Upsilon düğümleri (son iki yalnızca istisna işleme için kullanılır).

### Phi nodes and Pi nodes

Phi düğümleri, genel SSA soyutlamasının bir parçasıdır (bu kavramla tanış değilseniz yukarıdaki bağlantıya bakın). Julia IR'de bu düğümler şu şekilde temsil edilir:

```
struct PhiNode
    edges::Vector{Int32}
    values::Vector{Any}
end
```

her iki vektörün her zaman aynı uzunluğa sahip olmasını sağladığımız yer. Kanonik temsil (codegen ve yorumlayıcı tarafından işlenen) içinde, kenar değerleri, gelme ifadesi numaralarını gösterir (yani, eğer kenarın bir girişi `15` ise, bu phi düğümünü hedefleyen `15` numaralı ifadeden bir `goto`, `gotoifnot` veya örtük bir düşüş olmalıdır). Değerler ya SSA değerleri ya da sabitlerdir. Bir değerin atanmamış olması da mümkündür, eğer değişken bu yolda tanımlanmamışsa. Ancak, belirsizlik kontrolleri açıkça eklenir ve orta uç optimizasyonlardan sonra booleanlar olarak temsil edilir, bu nedenle kod üreticileri, bir Phi düğümünün herhangi bir kullanımının ilgili slotta atanmış bir değere sahip olacağını varsayabilir. Ayrıca, eşlemenin eksik olması da yasaldır, yani bir Phi düğümünün eksik gelen kenarları olabilir. Bu durumda, ilgili değerin kullanılmayacağının dinamik olarak garanti edilmesi gerekir.

Not edin ki SSA, ilgili öncülün terminatöründen sonra anlamsal olarak meydana gelir ("kenarında"). Sonuç olarak, bir temel bloğun başlangıcında birden fazla Phi düğümü varsa, bunlar aynı anda çalıştırılır. Bu, aşağıdaki IR kesitinde, eğer `23` bloğundan geldiğimizde, `%46`'nın bu bloğa girmeden önce `%45` ile ilişkili değeri alacağı anlamına gelir.

```julia
%45 = φ (#18 => %23, #23 => %50)
%46 = φ (#18 => 1.0, #23 => %45)
```

PiNodes, belirli bir pi düğümü tarafından domine edilen temel bloklarda varsayılan olarak kabul edilebilecek statik olarak kanıtlanmış bilgileri kodlar. Kavramsal olarak, [ABCD: Eliminating Array Bounds Checks on Demand](https://dl.acm.org/citation.cfm?id=358438.349342) makalesinde tanıtılan teknikle veya LLVM'deki predikat bilgi düğümleriyle eşdeğerdir. Nasıl çalıştıklarını görmek için, örneğin, dikkate alın.

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    # use x
else
    # use x
end
```

Önerme ekleme işlemi yapabiliriz ve bunu şu hale getirebiliriz:

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    %x_int = PiNode(x, Int)
    # use %x_int
else
    %x_float = PiNode(x, Float64)
    # use %x_float
end
```

Pi düğümleri genellikle yorumlayıcıda göz ardı edilir, çünkü değerler üzerinde herhangi bir etkisi yoktur, ancak bazen derleyicide kod üretimine yol açabilir (örneğin, örtük bir birleşim bölünmesi temsilinden düz bir kutusuz temsile geçmek için). Pi Düğümlerinin ana faydası, değerlerin yol koşullarının, bu koşullara önem veren çoğu optimizasyon için genellikle yapılan def-use zincir yürüyüşü ile basitçe biriktirilebilmesidir.

### PhiC nodes and Upsilon nodes

İstisna işleme, SSA hikayesini orta derecede karmaşık hale getirir, çünkü istisna işleme, IR'ye değerlerin izlenmesi gereken ek kontrol akışı kenarları ekler. Bunu yapmanın bir yolu, LLVM tarafından izlenen bir yaklaşımdır; bu yaklaşım, istisna fırlatabilecek çağrıları temel blok terminallerine yerleştirmek ve yakalama işleyicisine açık bir kontrol akışı kenarı eklemektir:

```
invoke @function_that_may_throw() to label %regular unwind to %catch

regular:
# Control flow continues here

catch:
# Exceptions go here
```

Ancak, bu Julia gibi bir dilde sorunludur, çünkü optimizasyon boru hattının başında hangi çağrıların hata vereceğini bilemeyiz. Her çağrının (Julia'da her ifade) hata vereceğini temkinli bir şekilde varsaymak zorunda kalırız. Bu, birkaç olumsuz etkiye sahip olacaktır. Bir yandan, her temel bloğun kapsamını esasen tek bir çağrı ile sınırlayarak, temel blok seviyesinde işlemlerin gerçekleştirilmesi amacını boşa çıkarır. Öte yandan, her catch temel bloğu `n*m` phi düğüm argümanına sahip olacaktır (`n`, kritik bölgede bulunan ifade sayısı, `m` ise catch bloğundaki canlı değerlerin sayısı).

Bunu aşmak için, `Upsilon` ve `PhiC` düğümlerinin bir kombinasyonunu kullanıyoruz (C, `catch` için yazılmıştır, IR güzel yazıcısında `φᶜ` olarak gösterilir, çünkü unicode alt simge c mevcut değildir). Bu düğümleri düşünmenin birkaç yolu vardır, ancak belki de en kolay yol, her `PhiC`'yi benzersiz bir store-many, read-once slot'tan yükleme olarak düşünmektir; `Upsilon` ise ilgili store işlemi olmaktadır. `PhiC`, kendi örtük slot'una depolayan tüm upsilon düğümlerinin bir operand listesine sahiptir. Ancak, `Upsilon` düğümleri hangi `PhiC` düğümüne depoladıklarını kaydetmez. Bu, SSA IR'nin geri kalanıyla daha doğal bir entegrasyon sağlamak için yapılır. Örneğin, bir `PhiC` düğümünün daha fazla kullanımı yoksa, onu silmek güvenlidir ve aynı şey bir `Upsilon` düğümü için de geçerlidir. Çoğu IR geçişinde, `PhiC` düğümleri `Phi` düğümleri gibi ele alınabilir. Kullanım-tanım zincirleri boyunca takip edilebilirler ve yeni `PhiC` düğümlerine ve yeni `Upsilon` düğümlerine (orijinal `Upsilon` düğümleriyle aynı yerlerde) yükseltilebilirler. Bu düzenlemenin sonucu, `Upsilon` düğümlerinin (ve `PhiC` argümanlarının) sayısının belirli bir değişkene atanan değerlerin sayısına (SSA dönüşümünden önce) orantılı olmasıdır; kritik bölgedeki ifade sayısına değil.

Bu şemayı uygulamada görmek için, fonksiyonu dikkate alın

```julia
@noinline opaque() = invokelatest(identity, nothing) # Something opaque
function foo()
    local y
    x = 1
    try
        y = 2
        opaque()
        y = 3
        error()
    catch
    end
    (x, y)
end
```

İlgili IR (alakasız türler çıkarılmış) şudur:

```
1 ─       nothing::Nothing
2 ─ %2  = $(Expr(:enter, #4))
3 ─ %3  = ϒ (false)
│   %4  = ϒ (#undef)
│   %5  = ϒ (1)
│   %6  = ϒ (true)
│   %7  = ϒ (2)
│         invoke Main.opaque()::Any
│   %9  = ϒ (true)
│   %10 = ϒ (3)
│         invoke Main.error()::Union{}
└──       $(Expr(:unreachable))::Union{}
4 ┄ %13 = φᶜ (%3, %6, %9)::Bool
│   %14 = φᶜ (%4, %7, %10)::Core.Compiler.MaybeUndef(Int64)
│   %15 = φᶜ (%5)::Core.Const(1)
└──       $(Expr(:leave, Core.SSAValue(2)))
5 ─       $(Expr(:pop_exception, :(%2)))::Any
│         $(Expr(:throw_undef_if_not, :y, :(%13)))::Any
│   %19 = Core.tuple(%15, %14)
└──       return %19
```

Özellikle, kritik bölgeye giren her değerin kritik bölgenin üstünde bir upsilon düğümü aldığını unutmayın. Bunun nedeni, catch bloklarının fonksiyonun dışından görünmeyen bir kontrol akışı kenarına sahip olarak kabul edilmesidir. Sonuç olarak, hiçbir SSA değeri catch bloklarını domine etmez ve tüm gelen değerler bir `φᶜ` düğümü aracılığıyla gelmek zorundadır.

## Main SSA data structure

Ana `SSAIR` veri yapısı tartışmaya değerdir. LLVM ve Webkit'in B3 IR'sinden ilham alır. Veri yapısının özü, ifadelerin düz bir vektörüdür. Her ifade, vektördeki konumuna dayalı olarak dolaylı olarak bir SSA değeri atanır (yani, idx 1'deki ifadenin sonucu `SSAValue(1)` kullanılarak erişilebilir vb.). Her SSA değeri için, ayrıca türünü de koruruz. SSA değerleri tanım gereği yalnızca bir kez atandığından, bu tür aynı zamanda ilgili indeksteki ifadenin sonuç türüdür. Ancak, bu temsil oldukça verimli olmasına rağmen (çünkü atamalar açıkça kodlanmak zorunda değildir), elbette sıralamanın anlamsal olarak önemli olduğu gerçeği bir dezavantaj taşır; bu nedenle yeniden sıralamalar ve eklemeler ifade numaralarını değiştirir. Ayrıca, kullanım listelerini tutmuyoruz (yani, bir tanımdan tüm kullanımlarına yürümek, bu haritayı açıkça hesaplamadan imkansızdır - tanım listeleri ise, ilgili ifadeyi indeksten arayarak bulmak kolaydır), bu nedenle LLVM tarzı RAUW (tüm kullanımları değiştirme) işlemi mevcut değildir.

Bunun yerine, aşağıdakileri yapıyoruz:

  * Ayrı bir düğüm tamponu tutuyoruz (bunların eklenme pozisyonu, karşılık gelen değerin türü ve düğümün kendisi dahil). Bu düğümler, ekleme tamponundaki oluşumlarına göre numaralandırılır ve değerleri IR'de hemen başka yerlerde kullanılabilir (yani, orijinal ifade listesindeki 12 ifade varsa, ilk yeni ifade `SSAValue(13)` olarak erişilebilir).
  * RAUW stilindeki işlemler, ilgili ifade indeksini değiştirme değerine ayarlayarak gerçekleştirilir.
  * Açıklamalar, ilgili ifadeyi `nothing` olarak ayarlayarak silinir (bu, esasen yukarıdakilerin özel bir durumudur).
  * Eğer silinen ifadenin herhangi bir kullanımı varsa, bunlar `nothing` olarak ayarlanacaktır.

`compact!` fonksiyonu, yukarıdaki veri yapısını, düğümlerin uygun yere yerleştirilmesi, önemsiz kopya yayılımı ve kullanımların değişen SSA değerlerine yeniden adlandırılması işlemlerini gerçekleştirerek sıkıştırır. Ancak, bu planın akıllıca kısmı, bu sıkıştırmanın sonraki geçişin bir parçası olarak tembel bir şekilde yapılabilmesidir. Çoğu optimizasyon geçişi, analiz veya değişiklikler yaparken, ifadeler listesinin tamamında yürümek zorundadır. İfade listesini yinelemek için kullanılabilecek bir `IncrementalCompact` yineleyicisi sağlıyoruz. Bu, gerekli sıkıştırmaları gerçekleştirecek ve düğümün yeni indeksini ve düğümü döndürecektir. Bu noktada, def-use zincirlerinde yürümek ve IR üzerinde herhangi bir değişiklik veya silme yapmak yasaldır (ancak ekleme yasaktır).

Bu düzenlemenin arkasındaki fikir, optimizasyon geçişlerinin ilgili belleğe dokunması gerektiği ve buna bağlı bellek erişim cezasını üstlenmesi gerektiği için, ek evrak işlerinin gerçekleştirilmesinin nispeten az bir ek yük getirmesi (ve bu veri yapılarını IR değişikliği sırasında sürdürmenin getirdiği yükten tasarruf etmesi) gerektiğidir.
