# [Constructors](@id man-constructors)

Yapıcılar [^1] yeni nesneler oluşturan fonksiyonlardır - özellikle, [Composite Types](@ref) örnekleri. Julia'da, tür nesneleri de yapıcı fonksiyonlar olarak hizmet eder: bir argüman demetine fonksiyon olarak uygulandıklarında kendilerinin yeni örneklerini oluştururlar. Bu, bileşik türler tanıtıldığında kısaca bahsedilmişti. Örneğin:

```jldoctest footype
julia> struct Foo
           bar
           baz
       end

julia> foo = Foo(1, 2)
Foo(1, 2)

julia> foo.bar
1

julia> foo.baz
2
```

Birçok tür için, yeni nesneler oluşturmak için alan değerlerini bir araya getirmek yeterlidir. Ancak, bazı durumlarda bileşik nesneler oluştururken daha fazla işlevsellik gereklidir. Bazen, argümanları kontrol ederek veya dönüştürerek, invariants zorunlu hale getirilmelidir. [Recursive data structures](https://en.wikipedia.org/wiki/Recursion_%28computer_science%29#Recursive_data_structures_.28structural_recursion.29), özellikle kendine referans verenler, önce eksik bir durumda oluşturulmadan ve ardından programatik olarak bütün hale getirilmeden temiz bir şekilde oluşturulamaz. Bazen, nesneleri sahip oldukları alanlardan daha az veya farklı türde parametrelerle oluşturmak sadece pratik bir durumdur. Julia'nın nesne oluşturma sistemi, bu durumların hepsini ve daha fazlasını ele alır.

[^1]: Nomenclature: while the term "constructor" generally refers to the entire function which constructs objects of a type, it is common to abuse terminology slightly and refer to specific constructor methods as "constructors". In such situations, it is generally clear from the context that the term is used to mean "constructor method" rather than "constructor function", especially as it is often used in the sense of singling out a particular method of the constructor from all of the others.

## [Outer Constructor Methods](@id man-outer-constructor-methods)

Bir yapıcı, Julia'daki diğer herhangi bir işlev gibi, genel davranışı yöntemlerinin birleşik davranışıyla tanımlanır. Bu nedenle, yeni yöntemler tanımlayarak bir yapıcıya işlevsellik ekleyebilirsiniz. Örneğin, `Foo` nesneleri için yalnızca bir argüman alan ve verilen değeri hem `bar` hem de `baz` alanları için kullanan bir yapıcı yöntemi eklemek istediğinizi varsayalım. Bu basit:

```jldoctest footype
julia> Foo(x) = Foo(x,x)
Foo

julia> Foo(1)
Foo(1, 1)
```

Sıfır argümanlı bir `Foo` yapıcı metodu ekleyebilir ve hem `bar` hem de `baz` alanları için varsayılan değerler sağlayabilirsiniz:

```jldoctest footype
julia> Foo() = Foo(0)
Foo

julia> Foo()
Foo(0, 0)
```

Burada sıfır argümanlı yapıcı yöntem, tek argümanlı yapıcı yöntemi çağırır; bu da otomatik olarak sağlanan iki argümanlı yapıcı yöntemi çağırır. Çok yakında netleşecek nedenlerden dolayı, normal yöntemler olarak tanımlanan ek yapıcı yöntemler *dış* yapıcı yöntemler olarak adlandırılır. Dış yapıcı yöntemler yalnızca başka bir yapıcı yöntemi, örneğin otomatik olarak sağlanan varsayılan olanları çağırarak yeni bir örnek oluşturabilir.

## [Inner Constructor Methods](@id man-inner-constructor-methods)

Dış yapıcı yöntemler, nesne oluşturma için ek kolaylık yöntemleri sağlama sorununu ele almakta başarılı olsa da, bu bölümün girişinde bahsedilen diğer iki kullanım durumunu ele almakta başarısızdır: değişmezlikleri zorlamak ve kendine referans veren nesnelerin oluşturulmasına izin vermek. Bu sorunlar için *iç* yapıcı yöntemlere ihtiyaç vardır. Bir iç yapıcı yöntemi, iki fark dışında dış yapıcı yöntemine benzer:

1. Bu, normal yöntemler gibi dışarıda değil, bir tür bildirim bloğunun içinde tanımlanmıştır.
2. Özel olarak mevcut olan [`new`](@ref) adlı bir işleve erişimi vardır; bu işlev, bloğun türünde nesneler oluşturur.

Örneğin, birinin ilk sayının ikinci sayıdan büyük olmaması koşuluna tabi olan bir çift gerçek sayı tutan bir tür tanımlamak istediğini varsayalım. Bunu şu şekilde tanımlayabiliriz:

```jldoctest pairtype
julia> struct OrderedPair
           x::Real
           y::Real
           OrderedPair(x,y) = x > y ? error("out of order") : new(x,y)
       end
```

Artık `OrderedPair` nesneleri yalnızca `x <= y` olacak şekilde oluşturulabilir:

```jldoctest pairtype; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> OrderedPair(1, 2)
OrderedPair(1, 2)

julia> OrderedPair(2,1)
ERROR: out of order
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] OrderedPair(::Int64, ::Int64) at ./none:4
 [3] top-level scope
```

Eğer tür `mutable` olarak tanımlanmış olsaydı, alan değerlerini doğrudan değiştirerek bu değişmezliği ihlal edebilirdiniz. Elbette, bir nesnenin iç yapısıyla izinsiz oynamak kötü bir uygulamadır. Siz (veya başka biri) daha sonra ek dış yapıcı yöntemler sağlayabilirsiniz, ancak bir tür tanımlandıktan sonra daha fazla iç yapıcı yöntem eklemenin bir yolu yoktur. Dış yapıcı yöntemler yalnızca diğer yapıcı yöntemleri çağırarak nesneler oluşturabileceğinden, nihayetinde bir nesne oluşturmak için bazı iç yapıcıların çağrılması gerekir. Bu, tanımlanan türün tüm nesnelerinin, türle sağlanan iç yapıcı yöntemlerden birine yapılan bir çağrı ile var olması gerektiğini garanti eder ve böylece bir türün değişmezliklerinin bir dereceye kadar uygulanmasını sağlar.

Eğer herhangi bir iç yapıcı yöntemi tanımlanmışsa, varsayılan bir yapıcı yöntemi sağlanmaz: ihtiyacınız olan tüm iç yapıcıları kendiniz sağladığınız varsayılır. Varsayılan yapıcı, nesnenin tüm alanlarını parametre olarak alan kendi iç yapıcı yönteminizi yazmakla eşdeğerdir (karşılık gelen alanın bir türü varsa, doğru türde olma kısıtlaması ile) ve bunları `new`'e geçirerek elde edilen nesneyi döndürür:

```jldoctest
julia> struct Foo
           bar
           baz
           Foo(bar,baz) = new(bar,baz)
       end

```

Bu beyan, açık bir iç yapıcı yöntemi olmadan `Foo` türünün önceki tanımıyla aynı etkiye sahiptir. Aşağıdaki iki tür eşdeğerdir - biri varsayılan bir yapıcı ile, diğeri açık bir yapıcı ile:

```jldoctest
julia> struct T1
           x::Int64
       end

julia> struct T2
           x::Int64
           T2(x) = new(x)
       end

julia> T1(1)
T1(1)

julia> T2(1)
T2(1)

julia> T1(1.0)
T1(1)

julia> T2(1.0)
T2(1)
```

İç yapıcı yöntemlerin sayısını mümkün olduğunca az tutmak iyi bir uygulamadır: yalnızca tüm argümanları açıkça alan ve temel hata kontrolü ve dönüşümünü zorlayanlar. Varsayılan değerler veya yardımcı dönüşümler sağlayan ek kolaylık yapıcı yöntemler, ağır yükü üstlenmek için iç yapıcıları çağıran dış yapıcılar olarak sağlanmalıdır. Bu ayrım genellikle oldukça doğaldır.

## Incomplete Initialization

Son olarak ele alınmamış olan nihai problem, kendine referans veren nesnelerin veya daha genel olarak, özyinelemeli veri yapılarının inşasıdır. Temel zorluğun hemen belirgin olmayabileceğini göz önünde bulundurarak, bunu kısaca açıklayalım. Aşağıdaki özyinelemeli tür bildirimini düşünün:

```jldoctest selfrefer
julia> mutable struct SelfReferential
           obj::SelfReferential
       end

```

Bu tür, yeterince zararsız görünebilir, ta ki bir örneğini nasıl oluşturacağınızı düşünene kadar. Eğer `a`, `SelfReferential`'ın bir örneği ise, o zaman ikinci bir örnek şu çağrı ile oluşturulabilir:

```julia-repl
julia> b = SelfReferential(a)
```

Ama bir `obj` alanı için geçerli bir değer sağlayacak hiçbir örnek yokken ilk örneği nasıl oluştururuz? Tek çözüm, `obj` alanı atanmış olmayan eksik bir `SelfReferential` örneği oluşturmaya izin vermek ve bu eksik örneği başka bir örneğin, örneğin kendisinin `obj` alanı için geçerli bir değer olarak kullanmaktır.

Tamamlanmamış olarak başlatılmış nesnelerin oluşturulmasına izin vermek için, Julia [`new`](@ref) fonksiyonunun, türün sahip olduğu alan sayısından daha az alan ile çağrılmasına izin verir; bu, belirtilmemiş alanların başlatılmamış olduğu bir nesne döndürür. İç yapıcı yöntem, tamamlanmamış nesneyi kullanarak, döndürmeden önce başlatmasını tamamlayabilir. İşte, örneğin, `SelfReferential` türünü tanımlamanın bir başka denemesi; bu sefer, `obj` alanlarının kendilerine işaret ettiği örnekler döndüren sıfır argümanlı bir iç yapıcı kullanarak:

```jldoctest selfrefer2
julia> mutable struct SelfReferential
           obj::SelfReferential
           SelfReferential() = (x = new(); x.obj = x)
       end

```

Bu yapıcının çalıştığını ve nesnelerin gerçekten kendine referans veren nesneler olarak oluşturulduğunu doğrulayabiliriz:

```jldoctest selfrefer2
julia> x = SelfReferential();

julia> x === x
true

julia> x === x.obj
true

julia> x === x.obj.obj
true
```

İç içe bir yapıcıdan tamamen başlatılmış bir nesne döndürmenin genellikle iyi bir fikir olduğu doğru olsa da, eksik başlatılmış nesneleri döndürmek de mümkündür:

```jldoctest incomplete
julia> mutable struct Incomplete
           data
           Incomplete() = new()
       end

julia> z = Incomplete();
```

Uninitialized alanlara erişim, hemen bir hata oluşturur; ancak, başlatılmamış alanlarla nesneler oluşturmanıza izin verilir:

```jldoctest incomplete
julia> z.data
ERROR: UndefRefError: access to undefined reference
```

Bu, sürekli olarak `null` değerlerini kontrol etme ihtiyacını ortadan kaldırır. Ancak, tüm nesne alanları referans değildir. Julia, bazı türleri "sade veri" olarak kabul eder; bu, verilerinin tamamının kendi içinde bulunduğu ve diğer nesnelere referans vermediği anlamına gelir. Sade veri türleri, ilkel türleri (örneğin, `Int`) ve diğer sade veri türlerinin değişmez yapılarını içerir (bkz. ayrıca: [`isbits`](@ref), [`isbitstype`](@ref)). Bir sade veri türünün başlangıç içeriği belirsizdir:

```julia-repl
julia> struct HasPlain
           n::Int
           HasPlain() = new()
       end

julia> HasPlain()
HasPlain(438103441441)
```

Düz veri türlerinin dizileri aynı davranışı sergiler.

Tamamlanmamış nesneleri iç yapıcılardan diğer işlevlere geçirebilir ve tamamlanmalarını devredebilirseniz:

```jldoctest
julia> mutable struct Lazy
           data
           Lazy(v) = complete_me(new(), v)
       end
```

Tam olarak tamamlanmamış nesnelerden dönen nesnelerle olduğu gibi, eğer `complete_me` veya onun çağrılan herhangi biri `Lazy` nesnesinin `data` alanına, başlatılmadan önce erişmeye çalışırsa, hemen bir hata fırlatılacaktır.

## Parametric Constructors

Parametrik türler, yapıcı hikayesine birkaç karmaşıklık ekler. [Parametric Types](@ref)'dan hatırlayalım ki, varsayılan olarak, parametrik bileşik türlerin örnekleri ya açıkça verilen tür parametreleri ile ya da yapıcıya verilen argümanların türleri tarafından ima edilen tür parametreleri ile oluşturulabilir. İşte bazı örnekler:

```jldoctest parametric; filter = r"Closest candidates.*\n  .*"
julia> struct Point{T<:Real}
           x::T
           y::T
       end

julia> Point(1,2) ## implicit T ##
Point{Int64}(1, 2)

julia> Point(1.0,2.5) ## implicit T ##
Point{Float64}(1.0, 2.5)

julia> Point(1,2.5) ## implicit T ##
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, ::T) where T<:Real at none:2

julia> Point{Int64}(1, 2) ## explicit T ##
Point{Int64}(1, 2)

julia> Point{Int64}(1.0,2.5) ## explicit T ##
ERROR: InexactError: Int64(2.5)
Stacktrace:
[...]

julia> Point{Float64}(1.0, 2.5) ## explicit T ##
Point{Float64}(1.0, 2.5)

julia> Point{Float64}(1,2) ## explicit T ##
Point{Float64}(1.0, 2.0)
```

Gördüğünüz gibi, açık tür parametreleri ile yapılan yapıcı çağrılarında, argümanlar varsayılan alan türlerine dönüştürülür: `Point{Int64}(1,2)` çalışır, ancak `Point{Int64}(1.0,2.5)` [`InexactError`](@ref) hatasını verirken `2.5`'i [`Int64`](@ref)'ye dönüştürmeye çalışır. Tür, yapıcı çağrısındaki argümanlar tarafından varsayıldığında, `Point(1,2)` gibi, o zaman argümanların türleri uyuşmalıdır - aksi takdirde `T` belirlenemez - ancak eşleşen türdeki herhangi bir gerçek argüman çifti genel `Point` yapıcısına verilebilir.

Burada gerçekten olan şey, `Point`, `Point{Float64}` ve `Point{Int64}`'ün hepsinin farklı yapıcı fonksiyonlar olmasıdır. Aslında, `Point{T}` her `T` tipi için ayrı bir yapıcı fonksiyondur. Herhangi bir açıkça sağlanmış iç yapıcı olmadan, `Point{T<:Real}` bileşen türünün beyanı, her olası `T<:Real` tipi için, normal parametreli varsayılan iç yapıcılar gibi davranan otomatik olarak bir iç yapıcı `Point{T}` sağlar. Ayrıca, aynı türde olmalıdırlar, gerçek argüman çiftlerini alan tek bir genel dış `Point` yapıcısı sağlar. Bu yapıcıların otomatik sağlanması, aşağıdaki açık beyanla eşdeğerdir:

```jldoctest parametric2
julia> struct Point{T<:Real}
           x::T
           y::T
           Point{T}(x,y) where {T<:Real} = new(x,y)
       end

julia> Point(x::T, y::T) where {T<:Real} = Point{T}(x,y);
```

Herhangi bir tanımın, işlediği yapıcı çağrısının biçimine benzediğini unutmayın. `Point{Int64}(1,2)` çağrısı, `struct` bloğu içindeki `Point{T}(x,y)` tanımını tetikleyecektir. Öte yandan, dış yapıcı bildirimi, yalnızca aynı gerçek türdeki değer çiftlerine uygulanan genel `Point` yapıcısı için bir yöntem tanımlar. Bu bildirim, açık tür parametreleri olmadan yapılan yapıcı çağrılarının, `Point(1,2)` ve `Point(1.0,2.5)` gibi çalışmasını sağlar. Yöntem bildirimi, argümanları aynı türde olma ile kısıtladığından, farklı türde argümanlar içeren `Point(1,2.5)` gibi çağrılar "hiçbir yöntem" hatalarına yol açar.

Varsayıyoruz ki `Point(1,2.5)` yapıcı çağrısını, tam sayı değeri `1`'i kayan nokta değeri `1.0`'a "terfi ettirerek" çalışır hale getirmek istiyoruz. Bunu başarmanın en basit yolu, aşağıdaki ek dış yapıcı yöntemini tanımlamaktır:

```jldoctest parametric2
julia> Point(x::Int64, y::Float64) = Point(convert(Float64,x),y);
```

Bu yöntem, [`convert`](@ref) fonksiyonunu kullanarak `x`'i açıkça [`Float64`](@ref)'ya dönüştürür ve ardından her iki argümanın da `4d61726b646f776e2e436f64652822222c2022466c6f617436342229_40726566` olduğu durum için genel yapıcıya inşaatı devreder. Bu yöntem tanımı ile daha önce [`MethodError`](@ref) olan şey artık `Point{Float64}` türünde bir nokta oluşturmayı başarıyla gerçekleştirir:

```jldoctest parametric2
julia> p = Point(1,2.5)
Point{Float64}(1.0, 2.5)

julia> typeof(p)
Point{Float64}
```

Ancak, diğer benzer aramalar hala çalışmıyor:

```jldoctest parametric2
julia> Point(1.5,2)
ERROR: MethodError: no method matching Point(::Float64, ::Int64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T<:Real
   @ Main none:1
  Point(!Matched::Int64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]
```

For a more general way to make all such calls work sensibly, see [Conversion and Promotion](@ref conversion-and-promotion). At the risk of spoiling the suspense, we can reveal here that all it takes is the following outer method definition to make all calls to the general `Point` constructor work as one would expect:

```jldoctest parametric2
julia> Point(x::Real, y::Real) = Point(promote(x,y)...);
```

`promote` fonksiyonu tüm argümanlarını ortak bir türe dönüştürür - bu durumda [`Float64`](@ref). Bu yöntem tanımı ile `Point` yapıcısı argümanlarını, [`+`](@ref) gibi sayısal operatörlerin yaptığı gibi yükseltir ve tüm gerçek sayılar için çalışır:

```jldoctest parametric2
julia> Point(1.5,2)
Point{Float64}(1.5, 2.0)

julia> Point(1,1//2)
Point{Rational{Int64}}(1//1, 1//2)

julia> Point(1.0,1//2)
Point{Float64}(1.0, 0.5)
```

Böylece, Julia'da varsayılan olarak sağlanan örtük tür parametreli yapıcılar oldukça katı olsa da, bunların daha rahat ama mantıklı bir şekilde davranmasını sağlamak oldukça kolaydır. Ayrıca, yapıcılar tür sisteminin, yöntemlerin ve çoklu dağıtımın tüm gücünden yararlanabildiğinden, karmaşık davranışları tanımlamak genellikle oldukça basittir.

## Case Study: Rational

Belki de bu parçaları bir araya getirmenin en iyi yolu, bir parametreli bileşik tür ve onun yapıcı yöntemleri ile ilgili gerçek bir dünya örneği sunmaktır. Bu amaçla, Julia'nın yerleşik [`Rational`](@ref) türüne benzer kendi rasyonel sayı türümüz `OurRational`'ı uyguluyoruz, tanımlandığı [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) :

```jldoctest rational
julia> struct OurRational{T<:Integer} <: Real
           num::T
           den::T
           function OurRational{T}(num::T, den::T) where T<:Integer
               if num == 0 && den == 0
                    error("invalid rational: 0//0")
               end
               num = flipsign(num, den)
               den = flipsign(den, den)
               g = gcd(num, den)
               num = div(num, g)
               den = div(den, g)
               new(num, den)
           end
       end

julia> OurRational(n::T, d::T) where {T<:Integer} = OurRational{T}(n,d)
OurRational

julia> OurRational(n::Integer, d::Integer) = OurRational(promote(n,d)...)
OurRational

julia> OurRational(n::Integer) = OurRational(n,one(n))
OurRational

julia> ⊘(n::Integer, d::Integer) = OurRational(n,d)
⊘ (generic function with 1 method)

julia> ⊘(x::OurRational, y::Integer) = x.num ⊘ (x.den*y)
⊘ (generic function with 2 methods)

julia> ⊘(x::Integer, y::OurRational) = (x*y.den) ⊘ y.num
⊘ (generic function with 3 methods)

julia> ⊘(x::Complex, y::Real) = complex(real(x) ⊘ y, imag(x) ⊘ y)
⊘ (generic function with 4 methods)

julia> ⊘(x::Real, y::Complex) = (x*y') ⊘ real(y*y')
⊘ (generic function with 5 methods)

julia> function ⊘(x::Complex, y::Complex)
           xy = x*y'
           yy = real(y*y')
           complex(real(xy) ⊘ yy, imag(xy) ⊘ yy)
       end
⊘ (generic function with 6 methods)
```

İlk satır – `struct OurRational{T<:Integer} <: Real` – `OurRational`'ın bir tamsayı türü parametresi aldığını ve kendisinin de bir reel tür olduğunu belirtir. Alan bildirimleri `num::T` ve `den::T`, bir `OurRational{T}` nesnesinde tutulan verilerin `T` türünde bir çift tamsayı olduğunu, birinin rasyonel değerin payını ve diğerinin paydasını temsil ettiğini gösterir.

Şimdi işler ilginçleşiyor. `OurRational`'ın, `num` ve `den`'in ikisinin de sıfır olmadığını kontrol eden ve her rasyonel sayının "en düşük terimlerde" ve negatif olmayan bir payda ile oluşturulmasını sağlayan tek bir iç yapıcı yöntemi vardır. Bu, önce paydanın negatif olması durumunda pay ve paydanın işaretlerini tersine çevirerek gerçekleştirilir. Ardından, her ikisi de en büyük ortak bölenleri ile bölünür (`gcd` her zaman, argümanlarının işaretine bakılmaksızın, negatif olmayan bir sayı döner). Bu, `OurRational` için tek iç yapıcı olduğundan, `OurRational` nesnelerinin her zaman bu normalleştirilmiş biçimde oluşturulacağından emin olabiliriz.

`OurRational` ayrıca kullanım kolaylığı için birkaç dış yapıcı yöntem sunar. İlki, pay ve paydanın aynı türde olduğu durumlarda tür parametresi `T`'yi pay ve paydanın türünden çıkaran "standart" genel yapıcıdır. İkincisi, verilen pay ve payda değerlerinin farklı türlere sahip olduğu durumlarda uygulanır: bunları ortak bir türe yükseltir ve ardından eşleşen türdeki argümanlar için dış yapıcıya inşaat delegasyonu yapar. Üçüncü dış yapıcı, tam sayı değerlerini, payda olarak `1` değeri sağlayarak rasyonellere dönüştürür.

Dış yapıcı tanımlamalarını takiben, `⊘` operatörü için bir dizi yöntem tanımladık; bu, rasyonelleri yazmak için bir sözdizimi sağlar (örneğin, `1 ⊘ 2`). Julia'nın `Rational` tipi bu amaç için [`//`](@ref) operatörünü kullanır. Bu tanımlamalardan önce, `⊘` tamamen tanımsız bir operatördür; yalnızca sözdizimi vardır ve anlamı yoktur. Sonrasında, [Rational Numbers](@ref)'da açıklandığı gibi davranır – tüm davranışı bu birkaç satırda tanımlanmıştır. `⊘`'nin infiks kullanımı, Julia'nın infiks operatörler olarak tanınan bir dizi sembole sahip olmasından dolayı çalışır. İlk ve en temel tanım, `a ⊘ b` ifadesinin, `a` ve `b` tam sayılar olduğunda `OurRational` yapıcısını uygulayarak bir `OurRational` oluşturmasını sağlar. `⊘`'nin operandlarından biri zaten bir rasyonel sayı olduğunda, sonuç oranı için yeni bir rasyonel oluşturma işlemi biraz farklıdır; bu davranış aslında bir rasyoneli bir tam sayıyla bölmeye eşdeğerdir. Son olarak, `⊘`'yi karmaşık integral değerlere uygulamak, `Complex{<:OurRational}` örneğini oluşturur – reel ve sanal kısımları rasyonel olan bir karmaşık sayı:

```jldoctest rational
julia> z = (1 + 2im) ⊘ (1 - 2im);

julia> typeof(z)
Complex{OurRational{Int64}}

julia> typeof(z) <: Complex{<:OurRational}
true
```

Böylece, `⊘` operatörü genellikle `OurRational` örneği döndürse de, eğer argümanlarından biri karmaşık tam sayılardan biriyse, bunun yerine `Complex{<:OurRational}` örneği döndürecektir. İlgilenen okuyucunun [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) belgesini gözden geçirmesi önerilir: kısa, kendi içinde yeterli ve tam bir temel Julia türünü uygulamaktadır.

## Outer-only constructors

Gördüğümüz gibi, tipik bir parametrik tür, tip parametreleri bilindiğinde çağrılan iç yapıcılara sahiptir; örneğin, `Point{Int}` için geçerlidir ancak `Point` için geçerli değildir. İsteğe bağlı olarak, tip parametrelerini otomatik olarak belirleyen dış yapıcılar eklenebilir; örneğin, `Point(1,2)` çağrısından `Point{Int}` oluşturmak. Dış yapıcılar, örnekleri gerçekten oluşturmak için iç yapıcıları çağırır. Ancak, bazı durumlarda, belirli tip parametrelerinin manuel olarak talep edilmesini istemediğiniz için iç yapıcılar sağlamamak daha iyi olabilir.

Örneğin, bir vektörü ve toplamının doğru bir temsilini saklayan bir tür tanımladığımızı varsayalım:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
SummedArray{Int32, Int32}(Int32[1, 2, 3], 6)
```

Sorun, `S`'nin `T`'den daha büyük bir tür olmasını istememizdir, böylece daha az bilgi kaybıyla birçok öğeyi toplayabiliriz. Örneğin, `T` [`Int32`](@ref) olduğunda, `S`'nin [`Int64`](@ref) olmasını isteriz. Bu nedenle, kullanıcının `SummedArray{Int32,Int32}` türünden örnekler oluşturmasına izin veren bir arayüzden kaçınmak istiyoruz. Bunu yapmanın bir yolu, yalnızca `SummedArray` için bir yapıcı sağlamaktır, ancak `struct` tanım bloğu içinde varsayılan yapıcıların oluşturulmasını engellemektir:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
           function SummedArray(a::Vector{T}) where T
               S = widen(T)
               new{T,S}(a, sum(S, a))
           end
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
ERROR: MethodError: no method matching SummedArray(::Vector{Int32}, ::Int32)
The type `SummedArray` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  SummedArray(::Vector{T}) where T
   @ Main none:4

Stacktrace:
[...]
```

Bu yapıcı, `SummedArray(a)` sözdizimi ile çağrılacaktır. `new{T,S}` sözdizimi, oluşturulacak tür için parametrelerin belirtilmesine olanak tanır; yani bu çağrı `SummedArray{T,S}` döndürecektir. `new{T,S}` herhangi bir yapıcı tanımında kullanılabilir, ancak kolaylık olması açısından `new{}` için parametreler, mümkün olduğunda oluşturulan türden otomatik olarak türetilir.

## Constructors are just callable objects

Herhangi bir türdeki bir nesne, bir yöntem tanımlayarak [made callable](@ref "Function-like objects") olabilir. Bu, türleri de içerir, yani [`Type`](@ref) türünde nesneler; ve yapıcılar aslında yalnızca çağrılabilir tür nesneleri olarak görülebilir. Örneğin, `Bool` üzerinde tanımlanmış birçok yöntem ve onun çeşitli üst türleri vardır:

```julia-repl
julia> methods(Bool)
# 10 methods for type constructor:
  [1] Bool(x::BigFloat)
     @ Base.MPFR mpfr.jl:393
  [2] Bool(x::Float16)
     @ Base float.jl:338
  [3] Bool(x::Rational)
     @ Base rational.jl:138
  [4] Bool(x::Real)
     @ Base float.jl:233
  [5] (dt::Type{<:Integer})(ip::Sockets.IPAddr)
     @ Sockets ~/tmp/jl/jl/julia-nightly-assert/share/julia/stdlib/v1.11/Sockets/src/IPAddr.jl:11
  [6] (::Type{T})(x::Enum{T2}) where {T<:Integer, T2<:Integer}
     @ Base.Enums Enums.jl:19
  [7] (::Type{T})(z::Complex) where T<:Real
     @ Base complex.jl:44
  [8] (::Type{T})(x::Base.TwicePrecision) where T<:Number
     @ Base twiceprecision.jl:265
  [9] (::Type{T})(x::T) where T<:Number
     @ boot.jl:894
 [10] (::Type{T})(x::AbstractChar) where T<:Union{AbstractChar, Number}
     @ char.jl:50
```

Alışılmış yapıcı sözdizimi, işlev benzeri nesne sözdizimi ile tam olarak eşdeğerdir, bu nedenle her iki sözdizimi ile bir yöntem tanımlamaya çalışmak, ilk yöntemin bir sonraki ile üzerine yazılmasına neden olacaktır:

```jldoctest
julia> struct S
           f::Int
       end

julia> S() = S(7)
S

julia> (::Type{S})() = S(8)  # overwrites the previous constructor method

julia> S()
S(8)
```
