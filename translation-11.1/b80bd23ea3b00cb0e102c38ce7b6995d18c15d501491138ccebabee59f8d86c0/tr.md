# `EscapeAnalysis`

`Core.Compiler.EscapeAnalysis`, bir derleyici yardımcı modülüdür ve [Julia's SSA-form IR](@ref Julia-SSA-form-IR) yani `IRCode`'un kaçış bilgilerini analiz etmeyi amaçlamaktadır.

Bu kaçış analizi şunları hedeflemektedir:

  * Julia'nın yüksek seviyeli anlamsal özelliklerinden yararlanarak, özellikle prosedürler arası çağrılar aracılığıyla kaçışlar ve takaslar hakkında düşünün.
  * çeşitli optimizasyonlar için kullanılabilecek kadar çok yönlü olun, bunlar arasında [alias-aware SROA](https://github.com/JuliaLang/julia/pull/43888), [early `finalize` insertion](https://github.com/JuliaLang/julia/pull/44056), [copy-free `ImmutableArray` construction](https://github.com/JuliaLang/julia/pull/42465), değiştirilebilir nesnelerin yığın tahsisi ve daha fazlası.
  * basit bir uygulama gerçekleştirin, tamamen geriye dönük veri akışı analizi uygulamasına dayalı olarak ve ortogonal ızgara özelliklerini birleştiren yeni bir ızgara tasarımı ile

## Try it out!

Kaçış analizini denemek için, test ve hata ayıklama amaçları için `code_escapes` ve `@code_escapes` kolaylık girişlerini tanımlayan `EAUtils.jl` yardımcı betiğini yükleyebilirsiniz:

```@repl EAUtils
let JULIA_DIR = normpath(Sys.BINDIR, "..", "share", "julia")
    # load `EscapeAnalysis` module to define the core analysis code
    include(normpath(JULIA_DIR, "base", "compiler", "ssair", "EscapeAnalysis", "EscapeAnalysis.jl"))
    using .EscapeAnalysis
    # load `EAUtils` module to define the utilities
    include(normpath(JULIA_DIR, "test", "compiler", "EscapeAnalysis", "EAUtils.jl"))
    using .EAUtils
end

mutable struct SafeRef{T}
    x::T
end
Base.getindex(x::SafeRef) = x.x;
Base.setindex!(x::SafeRef, v) = x.x = v;
Base.isassigned(x::SafeRef) = true;
get′(x) = isassigned(x) ? x[] : throw(x);

result = code_escapes((String,String,String,String)) do s1, s2, s3, s4
    r1 = Ref(s1)
    r2 = Ref(s2)
    r3 = SafeRef(s3)
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    s3 = get′(r3)       # still `r3` doesn't escape fully
    s4 = sizeof(s4)     # the argument `s4` doesn't escape here
    return s2, s3, s4
end
```

Her çağrı argümanı ve SSA ifadelerinin yanındaki semboller aşağıdaki anlamları temsil eder:

  * `◌` (düz): bu değer analiz edilmez çünkü bunun kaçış bilgisi her halükarda kullanılmayacaktır (örneğin nesne `isbitstype` olduğunda)
  * `✓` (yeşil veya camgöbeği): bu değer asla kaçmaz (`has_no_escape(result.state[x])` geçerlidir), arg kaçışı varsa mavi renkte (`has_arg_escape(result.state[x])` geçerlidir)
  * `↑` (mavi veya sarı): bu değer, çağırana dönüş ile kaçabilir (`has_return_escape(result.state[x])` geçerlidir), ayrıca işlenmemiş fırlatma kaçışı varsa sarı renkte (`has_thrown_escape(result.state[x])` geçerlidir)
  * `X` (kırmızı): bu değer, kaçış analizinin hakkında bir şeyler düşünemediği bir yere kaçabilir, örneğin global bir belleğe kaçış (`has_all_escape(result.state[x])` geçerlidir)
  * `*` (kalın): bu değerin kaçış durumu, [`EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo) kısmi sıralamasında `ReturnEscape` ve `AllEscape` arasında yer almaktadır, eğer işlenmemiş bir fırlatma kaçışı varsa sarı renkte gösterilir (`has_thrown_escape(result.state[x])` geçerlidir)
  * `′`: bu değer, `AliasInfo` özelliğinde ek nesne alanı / dizi elemanı bilgisi taşır.

Her arama argümanının ve SSA değerinin kaçış bilgisi programatik olarak aşağıdaki gibi incelenebilir:

```@repl EAUtils
result.state[Core.Argument(3)] # get EscapeInfo of `s2`

result.state[Core.SSAValue(3)] # get EscapeInfo of `r3`
```

## Analysis Design

### Lattice Design

`EscapeAnalysis`, [data-flow analysis](https://en.wikipedia.org/wiki/Data-flow_analysis) olarak uygulanmıştır ve [`x::EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo) latticesinde çalışır ve aşağıdaki özelliklerden oluşur:

  * `x.Analyzed::Bool`: resmi olarak lattice'in bir parçası değildir, sadece `x`'in analiz edilip edilmediğini gösterir.
  * `x.ReturnEscape::BitSet`: `x`'in çağırana dönüş yoluyla kaçabileceği SSA ifadelerini kaydeder.
  * `x.ThrownEscape::BitSet`: `x`'in istisna olarak atılabileceği SSA ifadelerini kaydeder (aşağıda açıklanan [exception handling](@ref EA-Exception-Handling) için kullanılır)
  * `x.AliasInfo`: `x`'in alanlarına veya dizi elemanlarına takma ad olarak atanabilecek tüm olası değerleri saklar (aşağıda açıklanan [alias analysis](@ref EA-Alias-Analysis) için kullanılır)
  * `x.ArgEscape::Int` (henüz uygulanmadı): argüman(lar) üzerinde `setfield!` ile çağırana kaçacağını belirtir.

Bu özellikler, bir giriş programının sonlu sayıda ifadeye sahip olduğu garantisiyle, sonlu bir yüksekliğe sahip kısmi bir ızgara oluşturmak için birleştirilebilir; bu, Julia'nın anlamsal özellikleriyle sağlanmaktadır. Bu ızgara tasarımının akıllıca kısmı, her ızgara özelliğini ayrı ayrı ele alarak ızgara işlemlerinin daha basit bir şekilde uygulanmasını sağlamasıdır[^LatticeDesign].

### Backward Escape Propagation

Bu kaçış analizi uygulaması, makalede tanımlanan veri akışı algoritmasına dayanmaktadır[^MM02]. Analiz, `EscapeInfo` ızgarasında çalışır ve her ızgara elemanının, analiz edilecek kalan SSA ifadelerine karşılık gelen program sayaçlarını içeren (kavramsal) bir çalışma kümesini koruyarak, alt seviyeden üst seviyeye geçiş yaparak sabit bir noktaya ulaşana kadar ızgara elemanlarını birleştirir. Analiz, her argümanın ve SSA ifadesinin `EscapeInfo`'sunu izleyen tek bir küresel durumu yönetir, ancak bazı akış duyarlılığının, gerektiğinde akış duyarlılığını düşünmek için daha sonra baskın analizle birleştirilebilecek `EscapeInfo`'nun `ReturnEscape` özelliğinde kaydedilen program sayaçları olarak kodlandığını da unutmayın.

Bu kaçış analizinin bir ayırt edici tasarımı, tamamen *geriye dönük* olmasıdır; yani kaçış bilgisi *kullanımlardan tanımlara* akar. Örneğin, aşağıdaki kod parçasında, EA önce `return %1` ifadesini analiz eder ve `%1` (karşılık gelen `obj`) üzerinde `ReturnEscape` uygular, ardından `%1 = %new(Base.RefValue{String, _2}))` ifadesini analiz eder ve `%1` üzerinde uygulanan `ReturnEscape`'i çağrı argümanı `_2` (karşılık gelen `s`) üzerine yayar.

```@repl EAUtils
code_escapes((String,)) do s
    obj = Ref(s)
    return obj
end
```

Buradaki ana gözlem, bu geriye dönük analizinin kaçış bilgilerinin kullanım-tanım zinciri boyunca doğal bir şekilde akmasına izin vermesidir, kontrol akışının aksine[^BackandForth]. Sonuç olarak, bu şema kaçış analizinin basit bir uygulamasını mümkün kılar; örneğin, `PhiNode` gibi bir yapı, bir `PhiNode` üzerindeki kaçış bilgilerini onun öncül değerlerine yayarak basit bir şekilde işlenebilir:

```@repl EAUtils
code_escapes((Bool, String, String)) do cnd, s, t
    if cnd
        obj = Ref(s)
    else
        obj = Ref(t)
    end
    return obj
end
```

### [Alias Analysis](@id EA-Alias-Analysis)

`EscapeAnalysis`, belirli bir doğrulukla nesne alanlarına uygulanan kaçışları değerlendirmek için geriye dönük bir alan analizi uygular ve `x::EscapeInfo`'nun `x.AliasInfo` özelliği bu amaçla mevcuttur. Bu özellik, "kullanım" yerlerinde `x`'in alanlarına takas edilebilecek tüm olası değerleri kaydeder ve ardından bu kaydedilen değerlerin kaçış bilgileri, "tanım" yerlerinde gerçek alan değerlerine aktarılır. Daha spesifik olarak, analiz, `getfield` çağrısını analiz ederek bir nesne alanına takas edilebilecek bir değeri kaydeder ve ardından `%new(...)` ifadesini veya `setfield!` çağrısını analiz ederken bu değerin kaçış bilgisini alana aktarır[^Dynamism].

```@repl EAUtils
code_escapes((String,)) do s
    obj = SafeRef("init")
    obj[] = s
    v = obj[]
    return v
end
```

Yukarıdaki örnekte, `%3` (karşılık gelen `v`) üzerinde uygulanan `ReturnEscape`, doğrudan `%1`'e (karşılık gelen `obj`) aktarılmamaktadır; bunun yerine `ReturnEscape` yalnızca `_2`'ye (karşılık gelen `s`) aktarılmaktadır. Burada `%3`, `%1`'in `AliasInfo` özelliğinde kaydedilir çünkü `%1`'in ilk alanına alias olabilmektedir ve ardından `Base.setfield!(%1, :x, _2)::String` analiz edilirken, bu kaçış bilgisi `_2`'ye aktarılır ancak `%1`'e aktarılmaz.

`EscapeAnalysis`, `getfield`-`%new`/`setfield!` zincirinde hangi IR öğelerinin takas edilebileceğini izler, böylece nesne alanlarının kaçışlarını analiz edebilir, ancak aslında bu takas analizi diğer IR öğelerini de ele alacak şekilde genelleştirilmelidir. Bunun nedeni, Julia IR'de aynı nesnenin bazen farklı IR öğeleriyle temsil edilmesidir ve bu nedenle aslında aynı nesneyi temsil edebilen bu farklı IR öğelerinin aynı kaçış bilgilerini paylaşmasını sağlamalıyız. Operandi olarak aynı nesneyi döndüren IR öğeleri, örneğin `PiNode` ve `typeassert`, bu IR düzeyindeki takasları oluşturabilir ve bu nedenle bu tür takas edilen değerler üzerindeki kaçış bilgisi aralarında paylaşılmalıdır. Daha ilginç bir şekilde, `PhiNode` üzerindeki mutasyonlar hakkında doğru bir şekilde düşünmek için de gereklidir. Aşağıdaki örneği ele alalım:

```@repl EAUtils
code_escapes((Bool, String,)) do cond, x
    if cond
        ϕ2 = ϕ1 = SafeRef("foo")
    else
        ϕ2 = ϕ1 = SafeRef("bar")
    end
    ϕ2[] = x
    y = ϕ1[]
    return y
end
```

`ϕ1 = %5` ve `ϕ2 = %6` takma adlandırılmıştır ve bu nedenle `%8 = Base.getfield(%6, :x)::String` (karşılık gelen `y = ϕ1[]`) üzerinde uygulanan `ReturnEscape`, `Base.setfield!(%5, :x, _3)::String` (karşılık gelen `ϕ2[] = x`) üzerine yayılmalıdır. Bu tür kaçış bilgilerinin doğru bir şekilde yayılabilmesi için, analiz, `ϕ1` ve `ϕ2`'nin *öncüllerinin* de takma adlandırılabileceğini ve kaçış bilgilerini eşitlemesi gerektiğini tanımalıdır.

Böyle bir takma ad bilgisiyle ilgili ilginç bir özellik, "kullanım" noktasında bilinmemesi, yalnızca "tanım" noktasında türetilebilmesidir (çünkü takma ad, kavramsal olarak atama ile eşdeğerdir) ve bu nedenle geriye dönük bir analize doğal olarak uymaz. İlgili değerler arasında kaçış bilgilerini verimli bir şekilde yaymak için, EscapeAnalysis.jl, eski bir JVM makalesinde açıklanan kaçış analizi algoritısından ilham alan bir yaklaşım kullanır[^JVM05]. Yani, kaçış lattice elemanlarını yönetmenin yanı sıra, analiz ayrıca "eşit"-takma ad kümesini, takma adlı argümanlar ve SSA ifadelerinin ayrık bir kümesini de sürdürmektedir. Takma ad kümesi, birbirine takma ad olabilen değerleri yönetir ve bu tür takma adlı değerlerden herhangi birine uygulanan kaçış bilgisinin aralarında eşitlenmesine olanak tanır.

### [Array Analysis](@id EA-Array-Analysis)

Yukarıda tanımlanan nesne alanları için takma ad analizi, dizi işlemlerini analiz etmek için de genelleştirilebilir. `EscapeAnalysis`, `arrayref`-`arrayset` kullanım-tanım zinciri aracılığıyla kaçışları iletecek şekilde çeşitli ilkel dizi işlemleri için işlemler uygular ve tahsis edilen dizilerin çok muhafazakar bir şekilde kaçmasına izin vermez:

```@repl EAUtils
code_escapes((String,)) do s
    ary = Any[]
    push!(ary, SafeRef(s))
    return ary[1], length(ary)
end
```

Yukarıdaki örnekte `EscapeAnalysis`, `%20` ve `%2` (tahsis edilen nesne `SafeRef(s)` ile ilgili) `arrayset`-`arrayref` zinciri aracılığıyla aliaslandığını anlar ve bunlar üzerinde `ReturnEscape` uygular, ancak tahsis edilen dizi `%1` ( `ary` ile ilgili) üzerinde bunu uygulamaz. `EscapeAnalysis` yine de `ary` üzerinde `ThrownEscape` uygular çünkü `BoundsError` aracılığıyla potansiyel kaçışları da hesaba katması gerekir, ancak bu tür işlenmemiş `ThrownEscape`'lerin genellikle `ary` tahsisini optimize ederken göz ardı edilebileceğini de belirtmek gerekir.

Ayrıca, dizi indeks bilgisi ve dizi boyutları *kesin olarak* bilindiğinde, `EscapeAnalysis`, `arrayref`-`arrayset` zinciri aracılığıyla "her bir eleman" aliasing hakkında bile düşünme yeteneğine sahiptir; çünkü `EscapeAnalysis`, nesneler için "her bir alan" alias analizini gerçekleştirir:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Vector{Any}(undef, 2)
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

Not edin ki `ReturnEscape` yalnızca `%2` (karşılık gelen `SafeRef(s)`) üzerinde uygulanmaktadır, ancak `%4` (karşılık gelen `SafeRef(t)`) üzerinde uygulanmamaktadır. Bunun nedeni, tahsis edilen dizinin boyutunun ve tüm `arrayref`/`arrayset` işlemleriyle ilgili indekslerin sabit bilgi olarak mevcut olması ve `EscapeAnalysis`'ın `%6`'nın `%2` ile alias olduğunu, ancak asla `%4` ile alias olamayacağını anlayabilmesidir. Bu tür bir durumda, sonraki optimizasyon geçişleri `Base.arrayref(true, %1, 1)::Any`'yi `%2` ile (diğer bir deyişle "yükleme-ileri alma") değiştirebilecek ve nihayetinde dizi `%1`'in tahsisatını tamamen ortadan kaldırabilecektir (diğer bir deyişle "skalar değiştirme").

Nesne alanı analizine kıyasla, nesne alanına erişim, çıkarım yoluyla elde edilen tür bilgisi kullanılarak basit bir şekilde analiz edilebilirken, dizi boyutu tür bilgisi olarak kodlanmamıştır ve bu nedenle bu bilgiyi elde etmek için ek bir analize ihtiyaç vardır. `EscapeAnalysis` şu anda, tahsis edilen dizilerin boyutlarını analiz etmek için ana analiz rutinini başlatmadan önce ek bir basit doğrusal tarama yapar, böylece sonraki kaçış analizi bu diziler üzerindeki işlemleri kesin bir şekilde analiz edebilir.

Ancak, bu tür hassas "öğe başına" takma ad analizi genellikle zordur. Temelde, dizinin doğasında gelen ana zorluk, dizi boyutunun ve indeksinin genellikle sabit olmamasıdır:

  * döngü sıklıkla döngü-variant, sabit olmayan dizi indeksleri üretir
  * (vektörlere özgü) dizi yeniden boyutlandırma, dizi boyutunu değiştirir ve sabitliğini geçersiz kılar.

Somut örneklerle bu zorlukları tartışalım.

Aşağıdaki örnekte, `EscapeAnalysis` kesin alias analizini başarısız kılıyor çünkü `Base.arrayset(false, %4, %8, %6)::Vector{Any}` içindeki indeks (basitçe) sabit değildir. Özellikle `Any[nothing, nothing]` bir döngü oluşturur ve bu `arrayset` işlemini bir döngü içinde çağırır, burada `%6` bir ϕ-düğüm değeri olarak temsil edilir (değeri kontrol akışına bağlıdır). Sonuç olarak, `ReturnEscape` hem `%23` ( `SafeRef(s)` ile ilgili) hem de `%25` ( `SafeRef(t)` ile ilgili) üzerinde uygulanır, ancak ideal olarak bunun yalnızca `%23` üzerinde uygulanmasını istiyoruz, `%25` üzerinde değil:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[nothing, nothing]
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

Sonraki örnek, vektör boyutlandırmanın kesin takma ad analizini nasıl zorlaştırdığını göstermektedir. Temel zorluk, tahsis edilen dizi `%1`'in ilk olarak `0` olarak başlatılmasıdır, ancak daha sonra iki `:jl_array_grow_end` çağrısıyla değişir. `EscapeAnalysis` şu anda herhangi bir dizi boyutlandırma işlemiyle karşılaştığında kesin takma ad analizinden vazgeçmektedir ve bu nedenle `%2` ( `SafeRef(s)` ile ilgili) ve `%20` ( `SafeRef(t)` ile ilgili) üzerinde `ReturnEscape` uygulanmaktadır:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[]
    push!(ary, SafeRef(s))
    push!(ary, SafeRef(t))
    ary[1], length(ary)
end
```

Bu zorlukları aşmak için, çıkarımın dizi boyutlarının farkında olması ve dizi boyutlarını akışa duyarlı bir şekilde yayması[^ArrayDimension] gerektiği gibi, döngü değişkeni değerlerinin güzel bir temsilini de bulmamız gerekiyor.

`EscapeAnalysis` şu anda dizi boyutları veya indeksleri basit bir şekilde sabit olmadığında, kesin indeks bilgilerini takip etmeyen daha belirsiz bir analize hızlıca geçiş yapar. Bu geçiş, veri akışı analizi çerçevesinde `EscapeInfo.AliasInfo` özelliğinin bir ızgara birleşim işlemi olarak doğal bir şekilde uygulanabilir.

### [Exception Handling](@id EA-Exception-Handling)

`EscapeAnalysis` istisnası yoluyla olası kaçışları nasıl ele aldığını belirtmek de önemlidir. Naif bir şekilde, `try` bloğunda atılabilecek tüm değerlere `:the_exception` nesnesine uygulanan kaçış bilgilerini yaymak yeterli gibi görünmektedir. Ancak, Julia'da `Base.current_exceptions` ve `rethrow` gibi istisna nesnesine erişmenin birkaç başka yolu vardır. Örneğin, aşağıdaki örnekte `r`'nin potansiyel kaçışını hesaba katmak için kaçış analizi gereklidir:

```@repl EAUtils
const GR = Ref{Any}();
@noinline function rethrow_escape!()
    try
        rethrow()
    catch err
        GR[] = err
    end
end;
get′(x) = isassigned(x) ? x[] : throw(x);

code_escapes() do
    r = Ref{String}()
    local t
    try
        t = get′(r)
    catch err
        t = typeof(err)   # `err` (which `r` aliases to) doesn't escape here
        rethrow_escape!() # but `r` escapes here
    end
    return t
end
```

Tüm olası kaçışları mevcut istisna arayüzleri aracılığıyla doğru bir şekilde değerlendirmek için küresel bir analiz gereklidir. Şu anda, üst düzey kaçış bilgilerini, potansiyel olarak fırlatılan tüm nesnelere temkinli bir şekilde iletmekteyiz, çünkü böyle bir ek analiz yapmak, istisna işleme ve hata yollarının genellikle çok performans duyarlı olması gerekmediği göz önüne alındığında, yapılmaya değer olmayabilir ve ayrıca hata yollarının optimizasyonları genellikle etkisiz olabilir, çünkü genellikle gecikme nedenleriyle "optimize edilmemiş" olarak bile tasarlanmışlardır.

`x::EscapeInfo`'nin `x.ThrownEscape` özelliği, `x`'in bir istisna olarak atılabileceği SSA ifadelerini kaydeder. Bu bilgiyi kullanarak `EscapeAnalysis`, her `try` bölgesinde atılabilecek olanlarla sınırlı olarak istisnalar aracılığıyla olası kaçışları yayabilir:

```@repl EAUtils
result = code_escapes((String,String)) do s1, s2
    r1 = Ref(s1)
    r2 = Ref(s2)
    local ret
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    return s2
end
```

## Analysis Usage

`analyze_escapes` SSA-IR öğelerinin kaçış bilgilerini analiz etmek için giriş noktasıdır.

Çoğu optimizasyon, SROA (`sroa_pass!`) gibi, inter-prosedürel çağrıları çözerek ve çağrılan kaynakları genişleterek inlining geçişi (`ssa_inlining_pass!`) tarafından basitleştirilmiş optimize edilmiş bir kaynağa uygulandığında daha etkilidir. Buna göre, `analyze_escapes` de inlining sonrası IR'yi analiz edebilir ve belirli bellekle ilgili optimizasyonlar için yararlı olan kaçış bilgilerini toplayabilir.

Ancak, inlining gibi belirli optimizasyon geçişleri kontrol akışlarını değiştirebileceği ve ölü kodu ortadan kaldırabileceği için, kaçış bilgilerin inter-prosedürel geçerliliğini bozabilir. Özellikle, inter-prosedürel olarak geçerli kaçış bilgilerini toplamak için, bir ön-inlining IR'yi analiz etmemiz gerekiyor.

Bu nedenle, `analyze_escapes` herhangi bir Julia düzeyindeki optimizasyon aşamasında `IRCode`'u analiz edebilir ve özellikle aşağıdaki iki aşamada kullanılması beklenmektedir:

  * `IPO EA`: önceden satır içi IR'yi analiz ederek IPO-geçerli kaçış bilgisi önbelleği oluşturma
  * `Yerel EA`: yerel olarak geçerli kaçış bilgilerini toplamak için post-inlining IR'yi analiz et

`IPO EA` tarafından türetilen kaçış bilgisi `ArgEscapeCache` veri yapısına dönüştürülür ve küresel olarak önbelleğe alınır. Uygun bir `get_escape_cache` geri çağrısını `analyze_escapes` fonksiyonuna geçirerek, kaçış analizi, önceki `IPO EA` tarafından türetilen, iç içe geçmiş çağrılara ait önbelleğe alınmış prosedürel bilgileri kullanarak analiz doğruluğunu artırabilir. Daha ilginç bir şekilde, `IPO EA` kaçış bilgilerini tür çıkarımı için kullanmak da geçerlidir; örneğin, çıkarım doğruluğu, değişken nesnenin `Const`/`PartialStruct`/`MustAlias` oluşturulmasıyla artırılabilir.

```@docs
Core.Compiler.EscapeAnalysis.analyze_escapes
Core.Compiler.EscapeAnalysis.EscapeState
Core.Compiler.EscapeAnalysis.EscapeInfo
```

---

[^LatticeDesign]: Our type inference implementation takes the alternative approach, where each lattice property is represented by a special lattice element type object. It turns out that it started to complicate implementations of the lattice operations mainly because it often requires conversion rules between each lattice element type object. And we are working on [overhauling our type inference lattice implementation](https://github.com/JuliaLang/julia/pull/42596) with `EscapeInfo`-like lattice design.

[^MM02]: *A Graph-Free approach to Data-Flow Analysis*.      Markas Mohnen, 2002, April.      [https://api.semanticscholar.org/CorpusID:28519618](https://api.semanticscholar.org/CorpusID:28519618).

[^BackandForth]: Our type inference algorithm in contrast is implemented as a forward analysis, because type information usually flows from "definition" to "usage" and it is more natural and effective to propagate such information in a forward way.

[^Dynamism]: In some cases, however, object fields can't be analyzed precisely. For example, object may escape to somewhere `EscapeAnalysis` can't account for possible memory effects on it, or fields of the objects simply can't be known because of the lack of type information. In such cases `AliasInfo` property is raised to the topmost element within its own lattice order, and it causes succeeding field analysis to be conservative and escape information imposed on fields of an unanalyzable object to be propagated to the object itself.

[^JVM05]: *Escape Analysis in the Context of Dynamic Compilation and Deoptimization*.       Thomas Kotzmann and Hanspeter Mössenböck, 2005, June.       [https://dl.acm.org/doi/10.1145/1064979.1064996](https://dl.acm.org/doi/10.1145/1064979.1064996).

[^ArrayDimension]: Otherwise we will need yet another forward data-flow analysis on top of the escape analysis.
