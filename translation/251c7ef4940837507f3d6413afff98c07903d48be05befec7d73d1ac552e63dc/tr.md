# [Conversion and Promotion](@id conversion-and-promotion)

Julia, matematik operatörlerinin argümanlarını ortak bir türe yükseltmek için bir sisteme sahiptir; bu, [Integers and Floating-Point Numbers](@ref), [Mathematical Operations and Elementary Functions](@ref), [Types](@ref man-types) ve [Methods](@ref) gibi çeşitli diğer bölümlerde bahsedilmiştir. Bu bölümde, bu yükseltme sisteminin nasıl çalıştığını, yeni türlere nasıl genişletileceğini ve yerleşik matematiksel operatörler dışında işlevlere nasıl uygulanacağını açıklıyoruz. Geleneksel olarak, programlama dilleri aritmetik argümanların yükseltilmesi konusunda iki gruba ayrılır:

  * **Yerleşik aritmetik türler ve operatörler için otomatik terfi.** Çoğu dilde, yerleşik sayısal türler, `+`, `-`, `*` ve `/` gibi infiks sözdizimi ile aritmetik operatörlere operand olarak kullanıldığında, beklenen sonuçları üretmek için otomatik olarak ortak bir türe terfi ettirilir. C, Java, Perl ve Python gibi diller, `1 + 1.5` toplamını, `+` operatörlerinden birinin bir tam sayı olmasına rağmen, doğru bir şekilde kayan nokta değeri `2.5` olarak hesaplar. Bu sistemler, programcıya görünmez olacak kadar dikkatlice tasarlanmış ve kullanışlıdır: böyle bir ifadeyi yazarken bu terfinin gerçekleştiğini bilinçli olarak düşünen pek kimse yoktur, ancak derleyiciler ve yorumlayıcılar, tam sayılar ve kayan nokta değerlerinin olduğu gibi eklenemeyeceği için toplama işleminden önce dönüşüm yapmak zorundadır. Bu tür otomatik dönüşümler için karmaşık kurallar, dolayısıyla bu dillerin spesifikasyonları ve uygulamaları için kaçınılmaz olarak bir parçasıdır.
  * **Otomatik terfi yok.** Bu kamp Ada ve ML'yi içerir - çok "katı" statik olarak tiplenmiş diller. Bu dillerde, her dönüşüm programcı tarafından açıkça belirtilmelidir. Bu nedenle, `1 + 1.5` ifadesi hem Ada hem de ML'de bir derleme hatası olacaktır. Bunun yerine, tam sayı `1`'i toplama işlemi yapmadan önce bir kayan nokta değerine açıkça dönüştürmek için `real(1) + 1.5` yazmak gerekir. Ancak her yerde açık dönüşüm yapmak o kadar elverişsizdir ki, hatta Ada'nın bile belirli bir otomatik dönüşüm derecesi vardır: tam sayı literalleri otomatik olarak beklenen tam sayı türüne yükseltilir ve kayan nokta literalleri de benzer şekilde uygun kayan nokta türlerine yükseltilir.

Bir anlamda, Julia "otomatik terfi yok" kategorisine girer: matematiksel operatörler, özel sözdizimi ile işlevlerdir ve işlevlerin argümanları asla otomatik olarak dönüştürülmez. Ancak, çeşitli karışık argüman türlerine matematiksel işlemler uygulamanın, polimorfik çoklu yönlendirme durumunun aşırı bir durumu olduğunu gözlemleyebilirsiniz - bu, Julia'nın yönlendirme ve tür sistemlerinin özellikle iyi başa çıktığı bir şeydir. Matematiksel operandların "otomatik" terfisi, özel bir uygulama olarak ortaya çıkar: Julia, bazı operand türü kombinasyonları için belirli bir uygulama mevcut olmadığında devreye giren matematiksel operatörler için önceden tanımlanmış genel yönlendirme kurallarına sahiptir. Bu genel kurallar, önce tüm operandları kullanıcı tanımlı terfi kurallarını kullanarak ortak bir türe terfi ettirir ve ardından sonuçta elde edilen değerler için, artık aynı türde olan, ilgili operatörün özel bir uygulamasını çağırır. Kullanıcı tanımlı türler, diğer türlere dönüştürme yöntemleri tanımlayarak ve diğer türlerle karıştıklarında hangi türlere terfi etmeleri gerektiğini tanımlayan birkaç terfi kuralı sağlayarak bu terfi sistemine kolayca katılabilir.

## Conversion

Belirli bir tür `T` değerini elde etmenin standart yolu, türün yapıcısını çağırmaktır, `T(x)`. Ancak, programcının bunu açıkça istemediği durumlarda bir değeri bir türden diğerine dönüştürmek uygun olabilir. Bir örnek, bir değeri bir diziye atamaktır: Eğer `A` bir `Vector{Float64}` ise, `A[1] = 2` ifadesi, `2`'yi `Int`'ten `Float64`'ye otomatik olarak dönüştürerek ve sonucu dizide saklayarak çalışmalıdır. Bu, [`convert`](@ref) fonksiyonu aracılığıyla yapılır.

`convert` fonksiyonu genellikle iki argüman alır: ilki bir tür nesnesi, ikincisi ise o türe dönüştürülecek bir değerdir. Döndürülen değer, verilen türün bir örneğine dönüştürülmüş değerdir. Bu fonksiyonu anlamanın en basit yolu, onu eylemde görmektir:

```jldoctest
julia> x = 12
12

julia> typeof(x)
Int64

julia> xu = convert(UInt8, x)
0x0c

julia> typeof(xu)
UInt8

julia> xf = convert(AbstractFloat, x)
12.0

julia> typeof(xf)
Float64

julia> a = Any[1 2 3; 4 5 6]
2×3 Matrix{Any}:
 1  2  3
 4  5  6

julia> convert(Array{Float64}, a)
2×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
```

Dönüşüm her zaman mümkün değildir; bu durumda [`MethodError`](@ref) atılır ve `convert`'in istenen dönüşümü nasıl gerçekleştireceğini bilmediğini belirtir:

```jldoctest
julia> convert(AbstractFloat, "foo")
ERROR: MethodError: Cannot `convert` an object of type String to an object of type AbstractFloat
[...]
```

Bazı diller, dizeleri sayılar olarak ayrıştırmayı veya sayıları dizeler olarak biçimlendirmeyi dönüşümler olarak kabul eder (birçok dinamik dil, dönüşümü sizin için otomatik olarak bile gerçekleştirebilir). Bu, Julia'da böyle değildir. Bazı dizeler sayılar olarak ayrıştırılabilse de, çoğu dize geçerli sayı temsilleri değildir ve yalnızca çok sınırlı bir alt kümesi geçerlidir. Bu nedenle, Julia'da bu işlemi gerçekleştirmek için özel [`parse`](@ref) fonksiyonu kullanılmalıdır, bu da işlemi daha belirgin hale getirir.

### When is `convert` called?

Aşağıdaki dil yapıları `convert` çağrısını yapar:

  * Diziye atama, dizinin eleman türüne dönüştürür.
  * Bir nesnenin bir alanına atama yapmak, alanın bildirilen türüne dönüştürür.
  * [`new`](@ref) nesnesinin tanımlı alan türlerine dönüştürülmesi.
  * Bir türü belirtilmiş bir değişkene atama (örneğin, `local x::T`) o türe dönüştürür.
  * Bir dönüş türü beyan edilmiş bir fonksiyon, dönüş değerini o türe dönüştürür.
  * [`ccall`](@ref) değerini geçmek, onu karşılık gelen argüman türüne dönüştürür.

### Conversion vs. Construction

`convert(T, x)` işlevinin davranışının `T(x)` ile neredeyse aynı olduğunu unutmayın. Gerçekten de genellikle öyledir. Ancak, önemli bir anlamsal fark vardır: `convert` örtük olarak çağrılabildiğinden, yöntemleri "güvenli" veya "şaşırtıcı olmayan" durumlarla sınırlıdır. `convert`, yalnızca aynı temel türdeki şeyleri temsil eden türler arasında dönüşüm yapar (örneğin, farklı sayı temsilleri veya farklı dize kodlamaları). Ayrıca genellikle kayıpsızdır; bir değeri farklı bir türe dönüştürmek ve tekrar geri döndürmek, tam olarak aynı değeri vermelidir.

Dört genel durumda yapıcılar `convert`'ten farklıdır:

#### Constructors for types unrelated to their arguments

Bazı yapıcılar "dönüşüm" kavramını uygulamaz. Örneğin, `Timer(2)` 2 saniyelik bir zamanlayıcı oluşturur, bu da gerçekten bir tam sayıdan bir zamanlayıcıya "dönüşüm" değildir.

#### Mutable collections

`convert(T, x)` orijinal `x`'i döndürmesi beklenir eğer `x` zaten `T` tipindeyse. Aksine, eğer `T` değiştirilebilir bir koleksiyon tipi ise, o zaman `T(x)` her zaman yeni bir koleksiyon oluşturmalıdır (elemanları `x`'den kopyalayarak).

#### Wrapper types

Bazı türler, diğer değerleri "saran" yapılar olduğunda, yapıcı, argümanını yeni bir nesne içine sarmış olabilir, bu argüman zaten istenen türde olsa bile. Örneğin, `Some(x)` ifadesi, bir değerin mevcut olduğunu belirtmek için `x`'i sarar (sonucun `Some` veya `nothing` olabileceği bir bağlamda). Ancak, `x` kendisi `Some(y)` nesnesi olabilir; bu durumda sonuç `Some(Some(y))` olur ve iki katmanlı bir sarma gerçekleşir. Öte yandan, `convert(Some, x)` ifadesi, `x` zaten bir `Some` olduğu için sadece `x`'i döndürür.

#### Constructors that don't return instances of their own type

*Çok nadir* durumlarda, `T(x)` yapıcısının `T` türünde olmayan bir nesne döndürmesi mantıklı olabilir. Bu, bir sarmalayıcı türün kendi tersine sahip olduğu durumlarda (örneğin, `Flip(Flip(x)) === x`) veya bir kütüphane yeniden yapılandırıldığında geriye dönük uyumluluk için eski bir çağrı sözdizimini desteklemek amacıyla olabilir. Ancak `convert(T, x)` her zaman `T` türünde bir değer döndürmelidir.

### Defining New Conversions

Yeni bir tür tanımlarken, başlangıçta onu oluşturmanın tüm yolları yapıcılar olarak tanımlanmalıdır. Eğer örtük dönüşümün faydalı olacağı ve bazı yapıcıların yukarıdaki "güvenlik" kriterlerini karşıladığı açıksa, o zaman `convert` yöntemleri eklenebilir. Bu yöntemler genellikle oldukça basittir, çünkü yalnızca uygun yapıcıyı çağırmaları gerekir. Böyle bir tanım şu şekilde görünebilir:

```julia
import Base: convert
convert(::Type{MyType}, x) = MyType(x)
```

Bu metodun ilk argümanının türü [`Type{MyType}`](@ref man-typet-type) olup, tek örneği `MyType`'dir. Bu nedenle, bu metod yalnızca ilk argüman `MyType` tür değeriyse çağrılır. İlk argüman için kullanılan sözdizimine dikkat edin: `::` sembolünden önce argüman adı atlanmış ve yalnızca tür verilmiştir. Bu, Julia'da türü belirtilmiş ancak değeri isimle referans verilmesine gerek olmayan bir fonksiyon argümanı için kullanılan sözdizimidir.

Tüm soy türlerin örnekleri varsayılan olarak "yeterince benzer" kabul edilir, bu nedenle Julia Base'te evrensel bir `convert` tanımı sağlanmıştır. Örneğin, bu tanım, herhangi bir `Number` türünü başka birine dönüştürmenin geçerli olduğunu belirtir; bu, 1-argümanlı bir yapıcı çağrılarak yapılır:

```julia
convert(::Type{T}, x::Number) where {T<:Number} = T(x)::T
```

Bu, yeni `Number` türlerinin yalnızca yapıcıları tanımlaması gerektiği anlamına gelir, çünkü bu tanım `convert` işlemini onlar için halledecektir. Zaten istenen türde olan argümanlar için bir kimlik dönüşümü de sağlanmıştır:

```julia
convert(::Type{T}, x::T) where {T<:Number} = x
```

Benzer tanımlar `AbstractString`, [`AbstractArray`](@ref) ve [`AbstractDict`](@ref) için mevcuttur.

## Promotion

Promosyon, karışık türlerin değerlerini tek bir ortak türe dönüştürmeyi ifade eder. Bu kesinlikle gerekli olmasa da, genellikle değerlerin dönüştürüldüğü ortak türün, tüm orijinal değerleri sadık bir şekilde temsil edebileceği varsayılır. Bu anlamda, "promosyon" terimi uygundur çünkü değerler "daha büyük" bir türe dönüştürülür - yani, tüm giriş değerlerini tek bir ortak türde temsil edebilen bir türe. Ancak, bunun nesne yönelimli (yapısal) süper türleme ile veya Julia'nın soyut süper türler kavramıyla karıştırılmaması önemlidir: promosyon, tür hiyerarşisi ile hiçbir ilgisi yoktur ve alternatif temsiller arasında dönüştürme ile tamamen ilgilidir. Örneğin, her [`Int32`](@ref) değeri, [`Float64`](@ref) değeri olarak da temsil edilebilir, ancak `Int32`, `Float64`'ün bir alt türü değildir.

Julia'da ortak bir "büyütme" türüne terfi, [`promote`](@ref) fonksiyonu ile gerçekleştirilir. Bu fonksiyon, herhangi bir sayıda argüman alır ve aynı sayıda değeri ortak bir türe dönüştürerek bir demet (tuple) döner veya terfi mümkün değilse bir istisna fırlatır. Terfi için en yaygın kullanım durumu, sayısal argümanları ortak bir türe dönüştürmektir:

```jldoctest
julia> promote(1, 2.5)
(1.0, 2.5)

julia> promote(1, 2.5, 3)
(1.0, 2.5, 3.0)

julia> promote(2, 3//4)
(2//1, 3//4)

julia> promote(1, 2.5, 3, 3//4)
(1.0, 2.5, 3.0, 0.75)

julia> promote(1.5, im)
(1.5 + 0.0im, 0.0 + 1.0im)

julia> promote(1 + 2im, 3//4)
(1//1 + 2//1*im, 3//4 + 0//1*im)
```

Kayan noktalı değerler, kayan nokta argüman türlerinin en büyüğüne yükseltilir. Tam sayılar, tam sayı argüman türlerinin en büyüğüne yükseltilir. Türler aynı boyutta ancak işaretlilik açısından farklıysa, işaretsiz tür seçilir. Tam sayılar ve kayan noktalı değerlerin karışımları, tüm değerleri tutacak kadar büyük bir kayan nokta türüne yükseltilir. Rasyonellerle karıştırılan tam sayılar, rasyonellere yükseltilir. Kayan noktalı değerlerle karıştırılan rasyoneller, kayan noktalara yükseltilir. Gerçek değerlerle karıştırılan karmaşık değerler, uygun türde karmaşık değere yükseltilir.

Bu, promosyonları kullanmanın gerçekten tek yolu. Geri kalan, akıllıca uygulama meselesidir; en tipik "akıllıca" uygulama, aritmetik operatörler `+`, `-`, `*` ve `/` gibi sayısal işlemler için genel yöntemlerin tanımlanmasıdır. İşte [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) içinde verilen bazı genel yöntem tanımları:

```julia
+(x::Number, y::Number) = +(promote(x,y)...)
-(x::Number, y::Number) = -(promote(x,y)...)
*(x::Number, y::Number) = *(promote(x,y)...)
/(x::Number, y::Number) = /(promote(x,y)...)
```

Bu yöntem tanımları, sayısal değer çiftlerini toplama, çıkarma, çarpma ve bölme için daha spesifik kuralların yokluğunda, değerleri ortak bir türe yükseltip tekrar denemek gerektiğini belirtir. İşte bu kadar basit: aritmetik işlemler için ortak bir sayısal türe yükseltme konusunda başka bir yerde endişelenmeye gerek yoktur - bu otomatik olarak gerçekleşir. [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) içinde bir dizi diğer aritmetik ve matematiksel fonksiyonlar için genel yükseltme yöntemlerinin tanımları bulunmaktadır, ancak bunun ötesinde, Julia Base'de `promote` çağrısına pek ihtiyaç yoktur. `promote`'un en yaygın kullanımları, karışık türlerle yapılan yapıcı çağrıların, alanları uygun bir ortak türe yükseltilmiş bir iç türe devretmesine olanak tanımak için sağlanan dış yapıcı yöntemlerde gerçekleşir. Örneğin, [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) aşağıdaki dış yapıcı yöntemini sağlar:

```julia
Rational(n::Integer, d::Integer) = Rational(promote(n,d)...)
```

Bu, aşağıdaki gibi çağrıların çalışmasına olanak tanır:

```jldoctest
julia> x = Rational(Int8(15),Int32(-5))
-3//1

julia> typeof(x)
Rational{Int32}
```

Çoğu kullanıcı tanımlı tür için, programcıların yapıcı işlevlere beklenen türleri açıkça sağlamalarını istemek daha iyi bir uygulamadır, ancak bazen, özellikle sayısal problemler için, otomatik olarak yükseltme yapmak kullanışlı olabilir.

### Defining Promotion Rules

Her ne kadar `promote` fonksiyonu için yöntemler doğrudan tanımlanabilse de, bu, tüm olası argüman türü permütasyonları için birçok gereksiz tanım gerektirecektir. Bunun yerine, `promote`'un davranışı, [`promote_rule`](@ref) adlı bir yardımcı fonksiyon cinsinden tanımlanmıştır; bu fonksiyon için yöntemler sağlanabilir. `promote_rule` fonksiyonu, bir çift tür nesnesi alır ve argüman türlerinin örneklerinin döndürülen türe terfi edeceği başka bir tür nesnesi döner. Böylece, kuralı tanımlayarak:

```julia
import Base: promote_rule
promote_rule(::Type{Float64}, ::Type{Float32}) = Float64
```

birinin, 64-bit ve 32-bit kayan nokta değerleri bir araya getirildiğinde, bunların 64-bit kayan nokta değerine yükseltilmesi gerektiğini belirtir. Yükseltme türü, argüman türlerinden biri olmak zorunda değildir. Örneğin, aşağıdaki yükseltme kuralları hem Julia Temelinde geçerlidir:

```julia
promote_rule(::Type{BigInt}, ::Type{Float64}) = BigFloat
promote_rule(::Type{BigInt}, ::Type{Int8}) = BigInt
```

Son durumunda, sonuç türü [`BigInt`](@ref)'dır çünkü `BigInt`, keyfi hassasiyetli tam sayı aritmetiği için yeterince büyük tam sayıları tutabilen tek türdür. Ayrıca, hem `promote_rule(::Type{A}, ::Type{B})` hem de `promote_rule(::Type{B}, ::Type{A})` tanımlamanıza gerek olmadığını unutmayın - simetri, `promote_rule`'ün terfi sürecinde nasıl kullanıldığıyla ima edilir.

`promote_rule` fonksiyonu, [`promote_type`](@ref) adlı ikinci bir fonksiyonu tanımlamak için bir yapı taşı olarak kullanılır. Bu fonksiyon, herhangi bir sayıdaki tür nesneleri verildiğinde, bu değerlerin `promote` fonksiyonuna argüman olarak verilmesi durumunda hangi ortak türe terfi edileceğini döndürür. Dolayısıyla, gerçek değerlerin yokluğunda, belirli türlerin bir koleksiyonunun hangi türe terfi edeceğini bilmek isteyen biri `promote_type` fonksiyonunu kullanabilir:

```jldoctest
julia> promote_type(Int8, Int64)
Int64
```

Not edin ki `promote_type`'ı doğrudan aşırı yüklemiyoruz: bunun yerine `promote_rule`'ı aşırı yüklüyoruz. `promote_type`, `promote_rule`'ı kullanır ve simetrikliği ekler. Bunu doğrudan aşırı yüklemek belirsizlik hatalarına neden olabilir. Aşırı yüklediğimiz `promote_rule`, şeylerin nasıl yükseltilmesi gerektiğini tanımlar ve bunu sorgulamak için `promote_type`'ı kullanırız.

İçsel olarak, `promote_type` `promote` içinde hangi tür argüman değerlerinin terfi için dönüştürülmesi gerektiğini belirlemek için kullanılır. Meraklı okuyucu, terfi mekanizmasını tanımlayan yaklaşık 35 satırda [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) kodunu okuyabilir.

### Case Study: Rational Promotions

Sonunda, Julia'nın rasyonel sayı türü ile ilgili devam eden vaka çalışmamızı tamamlıyoruz. Bu tür, aşağıdaki terfi kuralları ile terfi mekanizmasını nispeten sofistike bir şekilde kullanmaktadır:

```julia
import Base: promote_rule
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{Rational{S}}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:AbstractFloat} = promote_type(T,S)
```

İlk kural, bir rasyonel sayının herhangi bir başka tam sayı türü ile yükseltilmesinin, pay/payda türünün diğer tam sayı türü ile yükseltilmesinin sonucu olan bir rasyonel türüne yükseltileceğini belirtir. İkinci kural, iki farklı rasyonel sayı türüne aynı mantığı uygular ve sonuç olarak, ilgili pay/payda türlerinin yükseltilmesinin bir rasyonelini üretir. Üçüncü ve son kural, bir rasyoneli bir float ile yükseltmenin, pay/payda türünün float ile yükseltilmesiyle aynı türü vereceğini belirtir.

Bu küçük tanıtım kuralları, türün yapıcıları ve sayılar için varsayılan `convert` yöntemi ile birlikte, rasyonel sayıların Julia'nın diğer tüm sayısal türleri – tam sayılar, kayan nokta sayıları ve karmaşık sayılar – ile tamamen doğal bir şekilde etkileşimde bulunmasını sağlamak için yeterlidir. Uygun dönüşüm yöntemleri ve tanıtım kurallarını aynı şekilde sağlayarak, herhangi bir kullanıcı tanımlı sayısal tür, Julia'nın önceden tanımlanmış sayısallarıyla aynı şekilde doğal bir şekilde etkileşimde bulunabilir.
