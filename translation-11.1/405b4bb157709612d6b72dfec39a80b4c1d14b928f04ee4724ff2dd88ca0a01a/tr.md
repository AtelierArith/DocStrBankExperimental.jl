# Julia ASTs

Julia'nın iki kod temsili vardır. İlk olarak, parser tarafından döndürülen bir yüzey sözdizimi AST'si (örneğin, [`Meta.parse`](@ref) fonksiyonu) ve makrolar tarafından manipüle edilir. Bu, yazıldığı gibi kodun yapılandırılmış bir temsilidir ve bir karakter akışından `julia-parser.scm` tarafından oluşturulur. Sonra, tür çıkarımı ve kod üretimi tarafından kullanılan bir düşürülmüş form veya IR (ara temsil) vardır. Düşürülmüş formda daha az düğüm türü vardır, tüm makrolar genişletilmiştir ve tüm kontrol akışı açık dallara ve ifade dizilerine dönüştürülmüştür. Düşürülmüş form `julia-syntax.scm` tarafından oluşturulur.

Öncelikle makroları yazmak için gerekli olan AST'ye odaklanacağız.

## Surface syntax AST

Ön uç AST'leri neredeyse tamamen [`Expr`](@ref) ve atomlardan (örneğin semboller, sayılar) oluşur. Genellikle her görsel olarak farklı sözdizimsel form için farklı bir ifade başı vardır. Örnekler s-ifade sözdizimi ile verilecektir. Her parantezli liste bir Expr'e karşılık gelir, burada ilk öğe başlıktır. Örneğin `(call f x)` ifadesi Julia'daki `Expr(:call, :f, :x)` ifadesine karşılık gelir.

### Calls

| Input            | AST                                |
|:---------------- |:---------------------------------- |
| `f(x)`           | `(call f x)`                       |
| `f(x, y=1, z=2)` | `(call f x (kw y 1) (kw z 2))`     |
| `f(x; y=1)`      | `(call f (parameters (kw y 1)) x)` |
| `f(x...)`        | `(call f (... x))`                 |

`do` sözdizimi:

```julia
f(x) do a,b
    body
end
```

parses as `(do (call f x) (-> (tuple a b) (block body)))`.

### Operators

Çoğu operatör kullanımı sadece fonksiyon çağrılarıdır, bu nedenle `call` başlığı ile ayrıştırılır. Ancak bazı operatörler özel formlardır (mutlaka fonksiyon çağrıları değildir) ve bu durumlarda operatörün kendisi ifade başlığıdır. julia-parser.scm dosyasında bunlara "sentaktik operatörler" denir. Bazı operatörler (`+` ve `*`) N-ary ayrıştırma kullanır; zincirlenmiş çağrılar tek bir N-argüman çağrısı olarak ayrıştırılır. Son olarak, karşılaştırma zincirlerinin kendine özgü bir ifade yapısı vardır.

| Input       | AST                       |
|:----------- |:------------------------- |
| `x+y`       | `(call + x y)`            |
| `a+b+c+d`   | `(call + a b c d)`        |
| `2x`        | `(call * 2 x)`            |
| `a&&b`      | `(&& a b)`                |
| `x += 1`    | `(+= x 1)`                |
| `a ? 1 : 2` | `(if a 1 2)`              |
| `a,b`       | `(tuple a b)`             |
| `a==b`      | `(call == a b)`           |
| `1<i<=n`    | `(comparison 1 < i <= n)` |
| `a.b`       | `(. a (quote b))`         |
| `a.(b)`     | `(. a (tuple b))`         |

### Bracketed forms

| Input                    | AST                                             |
|:------------------------ |:----------------------------------------------- |
| `a[i]`                   | `(ref a i)`                                     |
| `t[i;j]`                 | `(typed_vcat t i j)`                            |
| `t[i j]`                 | `(typed_hcat t i j)`                            |
| `t[a b; c d]`            | `(typed_vcat t (row a b) (row c d))`            |
| `t[a b;;; c d]`          | `(typed_ncat t 3 (row a b) (row c d))`          |
| `a{b}`                   | `(curly a b)`                                   |
| `a{b;c}`                 | `(curly a (parameters c) b)`                    |
| `[x]`                    | `(vect x)`                                      |
| `[x,y]`                  | `(vect x y)`                                    |
| `[x;y]`                  | `(vcat x y)`                                    |
| `[x y]`                  | `(hcat x y)`                                    |
| `[x y; z t]`             | `(vcat (row x y) (row z t))`                    |
| `[x;y;; z;t;;;]`         | `(ncat 3 (nrow 2 (nrow 1 x y) (nrow 1 z t)))`   |
| `[x for y in z, a in b]` | `(comprehension (generator x (= y z) (= a b)))` |
| `T[x for y in z]`        | `(typed_comprehension T (generator x (= y z)))` |
| `(a, b, c)`              | `(tuple a b c)`                                 |
| `(a; b; c)`              | `(block a b c)`                                 |

### Macros

| Input         | AST                                          |
|:------------- |:-------------------------------------------- |
| `@m x y`      | `(macrocall @m (line) x y)`                  |
| `Base.@m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |
| `@Base.m x y` | `(macrocall (. Base (quote @m)) (line) x y)` |

### Strings

| Input           | AST                                 |
|:--------------- |:----------------------------------- |
| `"a"`           | `"a"`                               |
| `x"y"`          | `(macrocall @x_str (line) "y")`     |
| `x"y"z`         | `(macrocall @x_str (line) "y" "z")` |
| `"x = $x"`      | `(string "x = " x)`                 |
| ``` `a b c` ``` | `(macrocall @cmd (line) "a b c")`   |

Dokümantasyon dizesi sözdizimi:

```julia
"some docs"
f(x) = x
```

parses as `(macrocall (|.| Core '@doc) (line) "bazı belgeler" (= (call f x) (block x)))`.

### Imports and such

| Input               | AST                                 |
|:------------------- |:----------------------------------- |
| `import a`          | `(import (. a))`                    |
| `import a.b.c`      | `(import (. a b c))`                |
| `import ...a`       | `(import (. . . . a))`              |
| `import a.b, c.d`   | `(import (. a b) (. c d))`          |
| `import Base: x`    | `(import (: (. Base) (. x)))`       |
| `import Base: x, y` | `(import (: (. Base) (. x) (. y)))` |
| `export a, b`       | `(export a b)`                      |

`using` aynı temsile sahiptir `import`, ancak `:import` yerine `:using` ifade başlığı ile.

### Numbers

Julia, birçok şematik uygulamadan daha fazla sayı türünü destekler, bu nedenle tüm sayılar AST'de doğrudan şematik sayılar olarak temsil edilmez.

| Input                   | AST                                                      |
|:----------------------- |:-------------------------------------------------------- |
| `11111111111111111111`  | `(macrocall @int128_str nothing "11111111111111111111")` |
| `0xfffffffffffffffff`   | `(macrocall @uint128_str nothing "0xfffffffffffffffff")` |
| `1111...many digits...` | `(macrocall @big_str nothing "1111....")`                |

### Block forms

Bir ifade bloğu `(block stmt1 stmt2 ...)` olarak ayrıştırılır.

Eğer ifadesi:

```julia
if a
    b
elseif c
    d
else
    e
end
```

parses as:

```
(if a (block (line 2) b)
    (elseif (block (line 3) c) (block (line 4) d)
            (block (line 6 e))))
```

Bir `while` döngüsü `(while koşul gövde)` olarak ayrıştırılır.

Bir `for` döngüsü `(for (= var iter) body)` şeklinde ayrıştırılır. Eğer birden fazla yineleme spesifikasyonu varsa, bunlar bir blok olarak ayrıştırılır: `(for (block (= v1 iter1) (= v2 iter2)) body)`.

`break` ve `continue` 0-argüman ifadeleri olarak `(break)` ve `(continue)` şeklinde ayrıştırılır.

`let`, `(let (= var val) body)` veya `(let (block (= var1 val1) (= var2 val2) ...) body)` olarak ayrıştırılır, tıpkı `for` döngüleri gibi.

Temel bir fonksiyon tanımı `(function (call f x) body)` olarak ayrıştırılır. Daha karmaşık bir örnek:

```julia
function f(x::T; k = 1) where T
    return x+1
end
```

parses as:

```
(function (where (call f (parameters (kw k 1))
                       (:: x T))
                 T)
          (block (line 2) (return (call + x 1))))
```

Tür tanımı:

```julia
mutable struct Foo{T<:S}
    x::T
end
```

parses as:

```
(struct true (curly Foo (<: T S))
        (block (line 2) (:: x T)))
```

İlk argüman, türün değiştirilebilir olup olmadığını belirten bir boole'dir.

`try` blokları `(try try_block var catch_block finally_block)` olarak ayrıştırılır. Eğer `catch` sonrası bir değişken yoksa, `var` `#f` olur. Eğer `finally` ifadesi yoksa, o zaman son argüman mevcut değildir.

### Quote expressions

Julia kaynak sözdizimi biçimleri kod alıntısı için (`quote` ve `:( )`) `$` ile interpolasyonu destekler. Lisp terminolojisinde, bu onların aslında "arka alıntı" veya "yarı alıntı" biçimleri olduğu anlamına gelir. Dahili olarak, interpolasyonsuz kod alıntısı için de bir ihtiyaç vardır. Julia'nın şeması kodunda, interpolasyonsuz alıntı, `inert` ifade başlığı ile temsil edilir.

`inert` ifadeleri Julia `QuoteNode` nesnelerine dönüştürülür. Bu nesneler, herhangi bir türdeki tek bir değeri sarar ve değerlendirildiğinde basitçe o değeri döndürür.

Bir `quote` ifadesinin argümanı bir atom olduğunda, bu da bir `QuoteNode`'a dönüştürülür.

### Line numbers

Kaynak konum bilgisi `(satır satır_num dosya_adı)` şeklinde temsil edilir; burada üçüncü bileşen isteğe bağlıdır (ve mevcut satır numarası değiştiğinde, ancak dosya adı değişmediğinde, atlanır).

Bu ifadeler Julia'da `LineNumberNode` olarak temsil edilir.

### Macros

Makro hijyeni, `escape` ve `hygienic-scope` baş çiftinin ifadesiyle temsil edilir. Bir makro genişletmesinin sonucu, yeni kapsamın sonucunu temsil etmek için otomatik olarak `(hygienic-scope block module)` içine sarılır. Kullanıcı, çağırandan kodu içermek için içine `(escape block)` ekleyebilir.

## Lowered form

Düşürülmüş form (IR), derleyici için daha önemlidir, çünkü tür çıkarımı, iç içe geçme gibi optimizasyonlar ve kod üretimi için kullanılır. Ayrıca, insan için daha az belirgindir, çünkü girdi sözdiziminin önemli bir yeniden düzenlenmesinden kaynaklanır.

Aşağıdaki veri türleri, `Symbol` ve bazı sayı türlerine ek olarak, düşürülmüş formda mevcuttur:

  * `İfade`

    `head` alanı ile belirtilen bir düğüm türüne ve alt ifadelerin bir `Vector{Any}` olduğu bir `args` alanına sahiptir. Yüzey AST'sinin neredeyse her parçası bir `Expr` ile temsil edilirken, IR yalnızca sınırlı sayıda `Expr` kullanır, çoğunlukla çağrılar ve bazı yalnızca üst düzey formlar için.
  * `SlotNumarası`

    Argümanları ve yerel değişkenleri ardışık numaralandırma ile tanımlar. Slot indeksini veren bir tam sayı değerine sahip `id` alanı vardır. Bu slotların türleri, `CodeInfo` nesnelerinin `slottypes` alanında bulunabilir.
  * `Argüman`

    `SlotNumber` ile aynı, ancak yalnızca optimizasyondan sonra görünür. Referans verilen slotun, kapsayıcı fonksiyonun bir argümanı olduğunu belirtir.
  * `KodBilgisi`

    Bir dizi ifadenin IR'sini sarar. `code` alanı, yürütülecek ifadelerin bir dizisidir.
  * `GotoNode`

    Koşulsuz dal. Argüman, atlanacak kod dizisindeki bir indeks olarak temsil edilen dal hedefidir.
  * `GotoIfNot`

    Koşullu dal. Eğer `cond` alanı yanlış olarak değerlendirilirse, `dest` alanı tarafından tanımlanan indekse gider.
  * `ReturnNode`

    Argümanını ( `val` alanı) kapsayıcı fonksiyonun değeri olarak döndürür. Eğer `val` alanı tanımsızsa, bu ulaşılmaz bir ifadeyi temsil eder.
  * `AlıntıDüğümü`

    Bir değeri veri olarak referans almak için sarar. Örneğin, `f() = :a` fonksiyonu, sembol `a`nın döndürülmesi için `value` alanı sembol `a` olan bir `QuoteNode` içerir, böylece sembol kendisi değerlendirilmek yerine döndürülür.
  * `KüreselReferans`

    Modül `mod` içindeki global değişken `name`'e atıfta bulunur.
  * `SSAValue`

    Bir derleyici tarafından eklenen ardışık numaralandırılmış (1'den başlayarak) statik tek atama (SSA) değişkenini ifade eder. Bir `SSAValue`'ın numarası (`id`), temsil ettiği ifadenin değerinin kod dizisi indeksidir.
  * `YeniDeğişkenDüğümü`

    Bir değişkenin (slot) oluşturulduğu bir noktayı işaret eder. Bu, bir değişkenin tanımsız olarak sıfırlanması etkisini yaratır.

### `Expr` types

Bu semboller [`Expr`](@ref) alanının `head` kısmında küçük harflerle görünmektedir.

  * `arama`

    Fonksiyon çağrısı (dinamik dağıtım). `args[1]` çağrılacak fonksiyondur, `args[2:end]` ise argümanlardır.
  * `çağır`

    Fonksiyon çağrısı (statik yönlendirme). `args[1]` çağrılacak MethodInstance, `args[2:end]` ise argümanlardır (çağrılan fonksiyon `args[2]`'de bulunmaktadır).
  * `statik_parametre`

    Statik bir parametreyi indeksle referans al.
  * `=`

    Atama. IR'de, ilk argüman her zaman bir `SlotNumber` veya bir `GlobalRef`'dir.
  * `yöntem`

    Bir genel işlevine bir yöntem ekler ve gerekirse sonucu atar.

    1-argümanlı bir formu ve 3-argümanlı bir formu vardır. 1-argümanlı form, `function foo end` sözdiziminden kaynaklanır. 1-argümanlı formda, argüman bir semboldür. Eğer bu sembol mevcut kapsamda bir işlevi zaten adlandırıyorsa, hiçbir şey olmaz. Eğer sembol tanımsızsa, yeni bir işlev oluşturulur ve sembol tarafından belirtilen tanımlayıcıya atanır. Eğer sembol tanımlı ama bir işlevi adlandırmıyorsa, bir hata oluşur. "Bir işlevi adlandırmak" tanımının, bağlamanın sabit olduğu ve bir tekil tür nesnesine atıfta bulunduğu anlamına gelir. Bunun nedeni, bir tekil türün örneğinin, metoda eklenmesi gereken türü benzersiz bir şekilde tanımlamasıdır. Türün alanları olduğunda, metodun örneğe mi yoksa türüne mi eklendiği net olmayacaktır.

    3-argüman biçiminin aşağıdaki argümanları vardır:

      * `args[1]`

        Bir işlev adı veya bilinmiyorsa ya da gereksizse `nothing`. Eğer bir sembol ise, o zaman ifade ilk olarak yukarıdaki 1-argüman biçiminde davranır. Bu argüman o andan itibaren göz ardı edilir. Sadece türle katı bir şekilde yöntemler eklendiğinde `nothing` olabilir, `(::T)(x) = x`, veya mevcut bir işleve bir yöntem eklenirken, `MyModule.f(x) = x`.
      * `args[2]`

        Bir `SimpleVector` argüman türü verisi. `args[2][1]`, argüman türlerinin bir `SimpleVector`'ıdır ve `args[2][2]`, metodun statik parametrelerine karşılık gelen tür değişkenlerinin bir `SimpleVector`'ıdır.
      * `args[3]`

        Bir `CodeInfo`, metodun kendisi için. "Kapsam dışı" metod tanımları için (farklı kapsamlar içinde tanımlı metodları olan bir işleve bir metod eklemek) bu, bir `:lambda` ifadesine değerlendiren bir ifadedir.
  * `struct_type`

    Yeni bir `struct` tanımlayan 7-argüman ifadesi:

      * `args[1]`

        `struct`'un adı
      * `args[2]`

        Bir `call` ifadesi, parametrelerini belirterek bir `SimpleVector` oluşturur.
      * `args[3]`

        Bir `call` ifadesi, alan adlarını belirterek bir `SimpleVector` oluşturur.
      * `args[4]`

        Bir `Symbol`, `GlobalRef` veya `Expr`, süper türü belirtir (örneğin, `:Integer`, `GlobalRef(Core, :Any)` veya `:(Core.apply_type(AbstractArray, T, N))`)
      * `args[5]`

        Bir `call` ifadesi, alan türlerini belirterek bir `SimpleVector` oluşturur.
      * `args[6]`

        Bir Bool, `mutable` ise doğru.
      * `args[7]`

        Başlatmak için argüman sayısı. Bu, alan sayısı veya bir iç yapıcı'nın `new` ifadesiyle çağırdığı minimum alan sayısı olacaktır.
  * `soyut_tür`

    Yeni bir soyut tür tanımlayan 3-argümanlı bir ifade. Argümanlar, `struct_type` ifadelerinin 1, 2 ve 4 numaralı argümanlarıyla aynıdır.
  * `ilkel_tür`

    Yeni bir ilkel tür tanımlayan 4-argümanlı bir ifade. Argümanlar 1, 2 ve 4 `struct_type` ile aynıdır. Argüman 3, bit sayısını belirtir.

    !!! compat "Julia 1.5"
        `struct_type`, `abstract_type` ve `primitive_type` Julia 1.5'te kaldırıldı ve yeni yerleşik fonksiyonlara yapılan çağrılarla değiştirildi.
  * `küresel`

    Küresel bir bağlama bildirir.
  * `const`

    Bir (küresel) değişkeni sabit olarak tanımlar.
  * `yeni`

    Yeni bir yapı benzeri nesne ayırır. İlk argüman türdür. [`new`](@ref) sahte işlevi buna indirgenir ve tür her zaman derleyici tarafından eklenir. Bu, tamamen dahili bir özelliktir ve herhangi bir kontrol yapmaz. Rastgele `new` ifadelerini değerlendirmek kolayca segfault'a neden olabilir.
  * `splatnew`

    `new` ile benzer, ancak alan değerleri tek bir demet olarak geçilir. `new` birinci sınıf bir fonksiyon olsaydı, `splat(new)` ile benzer şekilde çalışır, bu yüzden bu ismi almıştır.
  * `tanımlı`

    `Expr(:isdefined, :x)` mevcut kapsamda `x`'in zaten tanımlanıp tanımlanmadığını belirten bir Bool döndürür.
  * `the_exception`

    `catch` bloğunun içindeki yakalanan istisnayı, `jl_current_exception(ct)` tarafından döndürüldüğü gibi verir.
  * `giriş`

    Bir istisna işleyicisi (`setjmp`) girer. `args[1]`, hata durumunda atlanacak yakalama bloğunun etiketidir. `pop_exception` tarafından tüketilen bir token verir.
  * `izin`

    Pop istisna yöneticileri. `args[1]` çıkarılacak yöneticilerin sayısıdır.
  * `pop_exception`

    Yakalayıcı bloğundan çıkarken, mevcut istisnaların yığınını ilişkili `enter` durumuna geri döndürün. `args[1]`, ilişkili `enter`'dan gelen belirteci içerir.

    !!! compat "Julia 1.1"
        `pop_exception` Julia 1.1'de yenidir.
  * `içeride`

    Kontroller, sınır kontrollerini açma veya kapama. Bir yığın tutulur; bu ifadenin ilk argümanı doğru veya yanlış ise (`doğru`, sınır kontrollerinin devre dışı olduğu anlamına gelir), yığına eklenir. İlk argüman `:pop` ise, yığın çıkarılır.
  * `boundscheck`

    `@inbounds` ile işaretlenmiş bir kod bölümüne yerleştirildiğinde `false` değerine sahiptir, aksi takdirde `true` değerine sahiptir.
  * `loopinfo`

    Bir döngünün sonunu işaret eder. `LowerSimdLoop`'a, ya `@simd` ifadesinin iç döngüsünü işaretlemek ya da LLVM döngü geçişlerine bilgi iletmek için geçirilen meta verileri içerir.
  * `copyast`

    Kısmi alıntı uygulamasının bir parçası. Argüman, basitçe kopyalanıp çalışma zamanında döndürülen bir yüzey sözdizimi AST'sidir.
  * `meta`

    Meta verisi. `args[1]` genellikle meta verisinin türünü belirten bir semboldür ve geri kalan argümanlar serbest biçimdedir. Aşağıdaki meta veri türleri yaygın olarak kullanılmaktadır:

      * `:inline` ve `:noinline`: Inline ipuçları.
  * `yabancı çağrı`

    Statik olarak hesaplanan `ccall` bilgileri için konteyner. Alanlar şunlardır:

      * `args[1]` : isim

        Yabancı işlev için ayrıştırılacak ifade.
      * `args[2]::Type` : RT

        İçinde bulunduğu metod tanımlandığında statik olarak hesaplanan (literal) dönüş türü.
      * `args[3]::SimpleVector` (of Types) : AT

        İçinde bulunduğu metod tanımlandığında statik olarak hesaplanan (literal) argüman türlerinin vektörü.
      * `args[4]::Int` : nreq

        Bir varargs fonksiyon tanımı için gereken argüman sayısı.
      * `args[5]::QuoteNode{Symbol}` : çağrı konvansiyonu

        Çağrı için çağrı düzeni.
      * `args[6:5+length(args[3])]` : argümanlar

        Tüm argümanlar için değerler (her birinin türü args[3] içinde verilmiştir).
      * `args[6+length(args[3])+1:end]` : gc-kökleri

        Çağrı süresi boyunca gc-rooted olması gerekebilecek ek nesneler. Bunların nereden türetildiği ve nasıl işlendiği için [Working with LLVM](@ref Working-with-LLVM) adresine bakın.
  * `yeni_opak_kapama`

    Yeni bir opak kapanış oluşturur. Alanlar şunlardır:

      * `args[1]` : imza

        Opak kapama işlevinin imzası. Opak kapamalar dağıtıma katılmaz, ancak girdi türleri kısıtlanabilir.
      * `args[2]` : isva

        Kapatmanın varargs'ı kabul edip etmediğini belirtir.
      * `args[3]` : lb

        Çıktı türü için alt sınır. (Varsayılan `Union{}`)
      * `args[4]` : ub

        Çıktı türü için üst sınır. (Varsayılan `Any`)
      * `args[5]` : yöntem

        Gerçek yöntem bir `opaque_closure_method` ifadesi olarak.
      * `args[6:end]` : yakalar

        Opak kapama tarafından yakalanan değerler.

    !!! compat "Julia 1.7"
        Opak kapalılar Julia 1.7'de eklendi.

### [Method](@id ast-lowered-method)

Tek bir yöntemin paylaşılan meta verilerini tanımlayan benzersiz bir kapsayıcı.

  * `isim`, `modül`, `dosya`, `satır`, `imza`

    Bilgisayar ve insan için yöntemi benzersiz şekilde tanımlayan meta veriler.
  * `belirsiz`

    Bu yöntemle belirsiz olabilecek diğer yöntemlerin önbelleği.
  * `uzmanlıklar`

    Bu Yöntem için oluşturulan tüm MethodInstance'ların önbelleği, benzersizliği sağlamak için kullanılır. Benzersizlik, özellikle artımlı ön derleme ve yöntem geçersiz kılma takibi için verimlilik açısından gereklidir.
  * `kaynak`

    Orijinal kaynak kodu (varsa, genellikle sıkıştırılmış).
  * `üreteç`

    Belirli bir yöntem imzası için özel kaynak almak üzere çalıştırılabilen bir çağrılabilir nesne.
  * `kökler`

    AST'ye interpolasyon yapılmış, AST'nin sıkıştırılması, tür çıkarımı veya yerel kod üretimi için gerekli olan AST dışındaki nesnelere işaretler.
  * `nargs`, `isva`, `called`, `is_for_opaque_closure`,

    Açıklayıcı bit alanları bu metodun kaynak kodu için.
  * `birincil_dünya`

    Bu Yöntemi "sahip" olan dünya yaşı.

### MethodInstance

Benzersiz bir kapsayıcı, bir Yöntem için tek bir çağrılabilir imzayı tanımlar. Özellikle [Proper maintenance and care of multi-threading locks](@ref Proper-maintenance-and-care-of-multi-threading-locks) bu alanları güvenli bir şekilde nasıl değiştireceğiniz hakkında önemli detaylar için.

  * `specTypes`

    Bu MethodInstance için birincil anahtar. Eşsizlik, `def.specializations` araması ile garanti edilir.
  * `def`

    Bu işlevin tanımladığı `Method`'in bir özel versiyonu. Ya da bu, bir Modül içinde genişletilmiş üst düzey bir Lambda ise ve bir Method'un parçası değilse, bir `Module`.
  * `sparam_vals`

    `specTypes` içindeki statik parametrelerin değerleri. `Method.unspecialized`'deki `MethodInstance` için bu, boş bir `SimpleVector`'dır. Ancak `MethodTable` önbelleğinden alınan bir çalışma zamanı `MethodInstance` için bu her zaman tanımlı ve indekslenebilir olacaktır.
  * `belirlenmemiş`

    Üst düzey bir thunk için sıkıştırılmamış kaynak kodu. Ayrıca, üretilen bir fonksiyon için, kaynak kodunun bulunabileceği birçok yerden biridir.
  * `geri kenarlar`

    Önceden tanımlanmış yöntemlerin tanımları sonrasında gerekli olabilecek artımlı yeniden analiz/yeniden derleme çalışmalarının verimli takibi için önbellek bağımlılıklarının ters listesini saklıyoruz. Bu, bu `MethodInstance`'a olası bir çağrı içerecek şekilde çıkarılan veya optimize edilen diğer `MethodInstance`'ların bir listesini tutarak çalışır. Bu optimizasyon sonuçları, `cache` içinde bir yerde saklanmış olabilir veya sabit yayılımı gibi önbelleğe almak istemediğimiz bir şeyin sonucu olabilir. Bu nedenle, burada çeşitli önbellek girişlerine tüm bu geri kenarları birleştiriyoruz (her durumda, max_world için bir sentinel değeri ile yalnızca bir uygulanabilir önbellek girişi vardır).
  * `önbellek`

    Bu şablon örneğini paylaşan `CodeInstance` nesnelerinin önbelleği.

### CodeInstance

  * `def`

    Bu önbellek girişinin türetildiği `MethodInstance`.
  * `sahip`

    Bu `CodeInstance`'ın sahibini temsil eden bir token. Eşleşmek için `jl_egal` kullanılacak.

  * `rettype`/`rettype_const`

    `specFunctionObject` alanı için çıkarılan dönüş türü, genellikle işlevin genel olarak hesaplanan dönüş türü ile de aynıdır.
  * `çıkarılan`

    Bu işlevin çıkarılan kaynağının bir önbelleğini içerebilir veya `rettype`'in çıkarıldığını belirtmek için sadece `nothing` olarak ayarlanmış olabilir.
  * `ftpr`

    Genel jlcall giriş noktası.
  * `jlcall_api`

    `fptr`'ı çağırırken kullanılacak ABI. Bazı önemli olanlar şunlardır:

      * 0 - Henüz derlenmedi
      * 1 - `JL_CALLABLE` `jl_value_t *(*)(jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 2 - Sabit (değer `rettype_const` içinde saklanır)
      * 3 - Statik parametreler ile iletilen `jl_value_t *(*)(jl_svec_t *sparams, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
      * 4 - Yorumlayıcıda çalıştır `jl_value_t *(*)(jl_method_instance_t *meth, jl_function_t *f, jl_value_t *args[nargs], uint32_t nargs)`
  * `min_dünya` / `max_dünya`

    Bu yöntem örneğinin çağrılabileceği dünya yaşları aralığı. Eğer max_world özel token değeri `-1` ise, değer henüz bilinmiyor. Yeniden düşünmemizi gerektiren bir geri kenar ile karşılaşana kadar kullanılmaya devam edilebilir.

### CodeInfo

A (genellikle geçici) kaynak kodunu tutmak için kullanılan bir konteyner.

  * `kod`

    Bir `Any` dizisi ifadeleri
  * `slotnames`

    Bir dizi sembol, her bir slot (argüman veya yerel değişken) için isimler verir.
  * `slotflags`

    Bir bit bayrağı olarak temsil edilen slot özelliklerinin `UInt8` dizisi:

      * 0x02 - atanmış (bu değişkenin solda hiçbir atama ifadesi yoksa yalnızca yanlış)
      * 0x08 - kullanıldı (slotun herhangi bir okuma veya yazma işlemi varsa)
      * 0x10 - statik olarak bir kez atanmış
      * 0x20 - atanmadan önce kullanılabilir. Bu bayrak yalnızca tür çıkarımından sonra geçerlidir.
  * `ssavaluetypes`

    Ya bir dizi ya da bir `Int`.

    Eğer bir `Int` ise, fonksiyondaki derleyici tarafından eklenen geçici konumların sayısını verir ( `code` dizisinin uzunluğu). Eğer bir dizi ise, her konum için bir tür belirtir.
  * `ssaflags`

    İfadelerdeki her bir ifade için 32 bitlik bayraklar. Daha fazla ayrıntı için julia.h dosyasındaki `jl_code_info_t` tanımına bakın.
  * `linetable`

    Bir kaynak konum nesneleri dizisi
  * `codelocs`

    `linetable` ile ilişkili her ifade için konumu belirten bir dizi tam sayı indeksi.

Opsiyonel Alanlar:

  * `slottypes`

    Slotlar için bir türler dizisi.
  * `rettype`

    Düşünülen döndürme türü, düşürülmüş formun (IR) varsayılan değeri `Any`'dir.
  * `çıkarım_sınır_heuristikleri_için_yöntem`

    `method_for_inference_heuristics`, gerektiğinde çıkarım sırasında verilen yöntemin jeneratörünü genişletecektir.
  * `ebeveyn`

    Bu nesneyi "sahiplenen" `MethodInstance` (varsa).
  * `kenarları`

    Yöntem örneklerinin geçersiz kılınması gereken ileri kenarları ilet.
  * `min_world`/`max_world`

    Bu kodun çıkarıldığı zaman geçerli olduğu dünya yaşları aralığı.

Boolean özellikleri:

  * `çıkarılan`

    Bu, tür çıkarımı tarafından üretilip üretilmediği.
  * `inlineable`

    Bu, iç içe geçme için uygun olup olmadığını belirleyip belirlememek.
  * `inboundları_yay`

    Bu, `@boundscheck` bloklarını atlamak amacıyla iç içe geçildiğinde `@inbounds`'un yayılıp yayılmaması gerektiğini belirler.

`UInt8` ayarları:

  * `constprop`

      * 0 = sezgisel kullanın
      * 1 = agresif
      * 2 = hiçbiri
  * `saflık` 5 bit bayrağından oluşturulmuştur:

      * 0x01 << 0 = bu yöntem tutarlı bir şekilde döndürmeyi veya sona ermeyi garanti eder (`:consistent`)
      * 0x01 << 1 = bu yöntem dışsal olarak anlamsal olarak görünür yan etkilerden ( `:effect_free` ) arındırılmıştır.
      * 0x01 << 2 = bu yöntem bir istisna fırlatmayacağı garanti edilir (`:nothrow`)
      * 0x01 << 3 = bu yöntem sonlanacağı garanti edilir (`:terminates_globally`)
      * 0x01 << 4 = bu yöntemdeki sözdizimsel kontrol akışının sona ereceği garanti edilmiştir (`:terminates_locally`)

    `Base.@assume_effects` için daha fazla ayrıntı için belgeleri inceleyin.
