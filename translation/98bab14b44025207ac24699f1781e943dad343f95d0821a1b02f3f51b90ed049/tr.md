# Methods

[Functions](@ref man-functions)'ten hatırlayın ki, bir fonksiyon, bir argüman demetini bir dönüş değerine eşleyen veya uygun bir değer döndürülemezse bir istisna fırlatan bir nesnedir. Aynı kavramsal fonksiyonun veya işlemin, farklı argüman türleri için oldukça farklı bir şekilde uygulanması yaygındır: iki tam sayıyı toplamak, iki kayan nokta sayısını toplamakla çok farklıdır; her ikisi de bir tam sayıyı bir kayan nokta sayısıyla toplamakla farklıdır. Uygulama farklılıklarına rağmen, bu işlemler "toplama" genel kavramı altında yer alır. Buna göre, Julia'da bu davranışların hepsi tek bir nesneye aittir: `+` fonksiyonu.

Farklı uygulamaların aynı kavramı sorunsuz bir şekilde kullanabilmesi için, fonksiyonlar bir anda tanımlanmak zorunda değildir; bunun yerine, belirli argüman türleri ve sayıları için belirli davranışlar sağlayarak parça parça tanımlanabilir. Bir fonksiyon için olası bir davranış tanımına *metot* denir. Şu ana kadar, tüm argüman türlerine uygulanabilir tek bir metotla tanımlanmış fonksiyon örnekleri sunduk. Ancak, metot tanımlarının imzaları, argümanların sayısının yanı sıra türlerini de belirtmek için anotasyonlanabilir ve birden fazla metot tanımı sağlanabilir. Bir fonksiyon belirli bir argüman demetine uygulandığında, o argümanlara en spesifik şekilde uygulanabilir metot uygulanır. Böylece, bir fonksiyonun genel davranışı, çeşitli metot tanımlarının davranışlarının bir yamanmasıdır. Eğer bu yama iyi tasarlanmışsa, metotların uygulamaları oldukça farklı olsa bile, fonksiyonun dışa dönük davranışı sorunsuz ve tutarlı görünecektir.

Uygulanan bir fonksiyonun hangi yönteminin yürütüleceğine karar verme sürecine *dağıtım* denir. Julia, dağıtım sürecinin bir fonksiyonun çağrılan yöntemini, verilen argüman sayısına ve fonksiyonun tüm argümanlarının türlerine göre seçmesine olanak tanır. Bu, geleneksel nesne yönelimli dillerden farklıdır; bu dillerde dağıtım yalnızca ilk argümana dayanarak gerçekleşir, bu genellikle özel bir argüman sözdizimine sahiptir ve bazen açıkça bir argüman olarak yazılmak yerine ima edilir. [^1] Bir fonksiyonun argümanlarının tümünü kullanarak hangi yöntemin çağrılması gerektiğini seçmek, yalnızca ilk argümanı kullanmaktan ziyade, [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch) olarak bilinir. Çoklu dağıtım, matematiksel kodlar için özellikle yararlıdır; çünkü işlemlerin "bir argümana" ait olduğunu yapay olarak belirlemek pek mantıklı değildir: `x + y` ifadesindeki toplama işlemi `x`'e, `y`'ye göre daha fazla mı aittir? Bir matematiksel operatörün uygulanması genellikle tüm argümanlarının türlerine bağlıdır. Ancak matematiksel işlemlerin ötesinde, çoklu dağıtım programları yapılandırmak ve organize etmek için güçlü ve kullanışlı bir paradigma haline gelir.

[^1]: In C++ or Java, for example, in a method call like `obj.meth(arg1,arg2)`, the object obj "receives" the method call and is implicitly passed to the method via the `this` keyword, rather than as an explicit method argument. When the current `this` object is the receiver of a method call, it can be omitted altogether, writing just `meth(arg1,arg2)`, with `this` implied as the receiving object.

!!! note
    Bu bölümdeki tüm örnekler, bir işlev için yöntemler tanımladığınızı varsayar *aynı* modülde. Eğer *başka* bir modülde bir işleve yöntem eklemek istiyorsanız, onu `import` etmeniz veya modül adlarıyla nitelendirilmiş ismini kullanmanız gerekir. [namespace management](@ref namespace-management) bölümüne bakın.


## Defining Methods

Şimdiye kadar, örneklerimizde yalnızca sınırsız argüman türlerine sahip tek bir yönteme sahip fonksiyonlar tanımladık. Bu fonksiyonlar, geleneksel dinamik olarak tiplenmiş dillerde olduğu gibi davranır. Bununla birlikte, çoklu dispatch ve yöntemleri neredeyse sürekli olarak kullanmışızdır; Julia'nın standart fonksiyonları ve operatörleri, daha önce bahsedilen `+` fonksiyonu gibi, argüman türü ve sayısının çeşitli olası kombinasyonları üzerindeki davranışlarını tanımlayan birçok yönteme sahiptir.

Bir fonksiyon tanımlarken, parametrelerin uygulanabilir olduğu türleri isteğe bağlı olarak kısıtlamak için `::` tür belirleme operatörünü kullanabilirsiniz; bu, [Composite Types](@ref) bölümünde tanıtılmıştır:

```jldoctest fofxy
julia> f(x::Float64, y::Float64) = 2x + y
f (generic function with 1 method)
```

Bu işlev tanımı yalnızca `x` ve `y`'nin her ikisi de [`Float64`](@ref) türünde değerler olduğu çağrılara uygulanır:

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0
```

Bunu diğer argüman türlerine uygulamak, [`MethodError`](@ref) ile sonuçlanacaktır:

```jldoctest fofxy
julia> f(2.0, 3)
ERROR: MethodError: no method matching f(::Float64, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(Float32(2.0), 3.0)
ERROR: MethodError: no method matching f(::Float32, ::Float64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, ::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(2.0, "3.0")
ERROR: MethodError: no method matching f(::Float64, ::String)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f("2.0", "3.0")
ERROR: MethodError: no method matching f(::String, ::String)
The function `f` exists, but no method is defined for this combination of argument types.
```

Gördüğünüz gibi, argümanlar tam olarak [`Float64`](@ref) türünde olmalıdır. Tam sayılar veya 32 bit kayan nokta değerleri gibi diğer sayısal türler otomatik olarak 64 bit kayan nokta değerine dönüştürülmez, ayrıca dizeler sayılar olarak ayrıştırılmaz. `Float64` somut bir tür olduğundan ve somut türler Julia'da alt sınıflara ayrılamadığından, böyle bir tanım yalnızca tam olarak `Float64` türünde olan argümanlara uygulanabilir. Ancak, beyan edilen parametre türlerinin soyut olduğu daha genel yöntemler yazmak genellikle faydalı olabilir:

```jldoctest fofxy
julia> f(x::Number, y::Number) = 2x - y
f (generic function with 2 methods)

julia> f(2.0, 3)
1.0
```

Bu yöntem tanımı, [`Number`](@ref) örnekleri olan herhangi bir argüman çiftine uygulanır. Her ikisi de aynı türde olmak zorunda değildir, yeter ki her biri sayısal değerler olsun. Farklı sayısal türleriyle başa çıkma problemi, `2x - y` ifadesindeki aritmetik işlemlere devredilmiştir.

Birden fazla yöntemi olan bir fonksiyonu tanımlamak için, fonksiyonu farklı sayı ve türdeki argümanlarla birden fazla kez tanımlamak yeterlidir. Bir fonksiyon için ilk yöntem tanımı, fonksiyon nesnesini oluşturur ve sonraki yöntem tanımları mevcut fonksiyon nesnesine yeni yöntemler ekler. Argümanların sayı ve türleriyle eşleşen en spesifik yöntem tanımı, fonksiyon uygulandığında yürütülecektir. Böylece, yukarıdaki iki yöntem tanımı bir arada, `f` için soyut `Number` türünün tüm örnek çiftleri üzerindeki davranışı tanımlar - ancak [`Float64`](@ref) değerlerine özgü farklı bir davranışla. Eğer argümanlardan biri 64 bit float ise ama diğeri değilse, o zaman `f(Float64,Float64)` yöntemi çağrılamaz ve daha genel olan `f(Number,Number)` yöntemi kullanılmalıdır:

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0

julia> f(2, 3.0)
1.0

julia> f(2.0, 3)
1.0

julia> f(2, 3)
1
```

The `2x + y` definition is only used in the first case, while the `2x - y` definition is used in the others. No automatic casting or conversion of function arguments is ever performed: all conversion in Julia is non-magical and completely explicit. [Conversion and Promotion](@ref conversion-and-promotion), however, shows how clever application of sufficiently advanced technology can be indistinguishable from magic. [^Clarke61]

Fonksiyon `f`, sayısal olmayan değerler ve iki argümandan az veya fazla argüman için tanımsız kalır ve uygulanması yine [`MethodError`](@ref) sonucunu verir:

```jldoctest fofxy
julia> f("foo", 3)
ERROR: MethodError: no method matching f(::String, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Number, ::Number)
   @ Main none:1
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f()
ERROR: MethodError: no method matching f()
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1
  f(!Matched::Number, !Matched::Number)
   @ Main none:1

Stacktrace:
[...]
```

Bir işlevin hangi yöntemlerinin mevcut olduğunu, etkileşimli bir oturumda işlev nesnesini kendisi yazarak kolayca görebilirsiniz:

```jldoctest fofxy
julia> f
f (generic function with 2 methods)
```

Bu çıktı, `f`'nin iki yöntemi olan bir fonksiyon nesnesi olduğunu bize söylüyor. O yöntemlerin imzalarının ne olduğunu bulmak için [`methods`](@ref) fonksiyonunu kullanın:

```jldoctest fofxy
julia> methods(f)
# 2 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
```

`f`'nin iki yöntemi olduğunu gösterir; biri iki `Float64` argümanı alırken, diğeri `Number` türünde argümanlar alır. Ayrıca, yöntemlerin tanımlandığı dosya ve satır numarasını belirtir: bu yöntemler REPL'de tanımlandığı için, görünür satır numarası `none:1` olarak alınır.

`::` ile bir tür bildirimi yoksa, bir yöntem parametresinin türü varsayılan olarak `Any`dir, bu da sınırlı olmadığı anlamına gelir çünkü Julia'daki tüm değerler `Any` soyut türünün örnekleridir. Bu nedenle, `f` için bir genel yöntem tanımlayabiliriz:

```jldoctest fofxy
julia> f(x,y) = println("Whoa there, Nelly.")
f (generic function with 3 methods)

julia> methods(f)
# 3 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
 [3] f(x, y)
     @ none:1

julia> f("foo", 1)
Whoa there, Nelly.
```

Bu genel yakalama, bir dizi parametre değeri için olası diğer yöntem tanımlarından daha az spesifiktir, bu nedenle yalnızca başka hiçbir yöntem tanımının uygulanmadığı argüman çiftleri üzerinde çağrılacaktır.

Üçüncü yöntemin imzasında, `x` ve `y` argümanları için herhangi bir tür belirtilmediğine dikkat edin. Bu, `f(x::Any, y::Any)` ifadesinin kısaltılmış bir yoludur.

Her ne kadar basit bir kavram gibi görünse de, değerlerin türleri üzerinde çoklu dağıtım, muhtemelen Julia dilinin en güçlü ve merkezi özelliğidir. Temel işlemler genellikle onlarca metoda sahiptir:

```julia-repl
julia> methods(+)
# 180 methods for generic function "+":
[1] +(x::Bool, z::Complex{Bool}) in Base at complex.jl:227
[2] +(x::Bool, y::Bool) in Base at bool.jl:89
[3] +(x::Bool) in Base at bool.jl:86
[4] +(x::Bool, y::T) where T<:AbstractFloat in Base at bool.jl:96
[5] +(x::Bool, z::Complex) in Base at complex.jl:234
[6] +(a::Float16, b::Float16) in Base at float.jl:373
[7] +(x::Float32, y::Float32) in Base at float.jl:375
[8] +(x::Float64, y::Float64) in Base at float.jl:376
[9] +(z::Complex{Bool}, x::Bool) in Base at complex.jl:228
[10] +(z::Complex{Bool}, x::Real) in Base at complex.jl:242
[11] +(x::Char, y::Integer) in Base at char.jl:40
[12] +(c::BigInt, x::BigFloat) in Base.MPFR at mpfr.jl:307
[13] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt, e::BigInt) in Base.GMP at gmp.jl:392
[14] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt) in Base.GMP at gmp.jl:391
[15] +(a::BigInt, b::BigInt, c::BigInt) in Base.GMP at gmp.jl:390
[16] +(x::BigInt, y::BigInt) in Base.GMP at gmp.jl:361
[17] +(x::BigInt, c::Union{UInt16, UInt32, UInt64, UInt8}) in Base.GMP at gmp.jl:398
...
[180] +(a, b, c, xs...) in Base at operators.jl:424
```

Çoklu dispatch ve esnek parametrik tür sistemi, Julia'nın yüksek seviyeli algoritmaları uygulama detaylarından bağımsız bir şekilde soyut olarak ifade etme yeteneğini kazandırır.

## [Method specializations](@id man-method-specializations)

Bir fonksiyonun birden fazla yöntemini oluşturduğunuzda, bu bazen "özelleştirme" olarak adlandırılır. Bu durumda, *fonksiyonu* ek yöntemler ekleyerek özelleştiriyorsunuz: her yeni yöntem, fonksiyonun yeni bir özelleştirmesidir. Yukarıda gösterildiği gibi, bu özelleştirmeler `methods` ile döndürülür.

Programcı müdahalesi olmadan gerçekleşen başka bir uzmanlaşma türü vardır: Julia'nın derleyicisi, kullanılan belirli argüman türleri için *metodu* otomatik olarak uzmanlaştırabilir. Bu tür uzmanlaşmalar `methods` ile listelenmez, çünkü bu yeni `Method`'lar oluşturmaz, ancak [`@code_typed`](@ref) gibi araçlar, bu tür uzmanlaşmaları incelemenizi sağlar.

Örneğin, bir yöntem oluşturursanız

```
mysum(x::Real, y::Real) = x + y
```

`mysum` fonksiyonuna bir yeni yöntem (muhtemelen tek yöntemi) verdiniz ve bu yöntem herhangi bir çift `Gerçek` sayı girişi alıyor. Ama sonra eğer yürütürseniz

```julia-repl
julia> mysum(1, 2)
3

julia> mysum(1.0, 2.0)
3.0
```

Julia, `mysum`'ı iki kez derleyecek, bir kez `x::Int, y::Int` için ve bir kez de `x::Float64, y::Float64` için. İki kez derlemenin amacı performanstır: `mysum`'ın kullandığı `+` için çağrılan yöntemler, `x` ve `y`'nin belirli türlerine bağlı olarak değişir ve farklı özel durumları derleyerek Julia, tüm yöntem aramalarını önceden yapabilir. Bu, programın çok daha hızlı çalışmasını sağlar, çünkü çalışırken yöntem aramasıyla uğraşmak zorunda kalmaz. Julia'nın otomatik özel durumu, genel algoritmalar yazmanıza ve derleyicinin ihtiyaç duyduğunuz her durum için verimli, özel kod üretmesini beklemenize olanak tanır.

Potansiyel uzmanlıkların sayısının etkili bir şekilde sınırsız olabileceği durumlarda, Julia bu varsayılan uzmanlıktan kaçınabilir. Daha fazla bilgi için [Be aware of when Julia avoids specializing](@ref)'ya bakın.

## [Method Ambiguities](@id man-ambiguities)

Bir dizi fonksiyon yöntemi tanımlamak mümkündür ki bazı argüman kombinasyonlarına uygulanabilir en özel yöntem benzersiz değildir:

```jldoctest gofxy
julia> g(x::Float64, y) = 2x + y
g (generic function with 1 method)

julia> g(x, y::Float64) = x + 2y
g (generic function with 2 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
ERROR: MethodError: g(::Float64, ::Float64) is ambiguous.

Candidates:
  g(x, y::Float64)
    @ Main none:1
  g(x::Float64, y)
    @ Main none:1

Possible fix, define
  g(::Float64, ::Float64)

Stacktrace:
[...]
```

Burada `g(2.0, 3.0)` çağrısı ya `g(::Float64, ::Any)` ya da `g(::Any, ::Float64)` yöntemi tarafından işlenebilir. Yöntemlerin tanımlanma sırası önemli değildir ve hiçbiri diğerinden daha spesifik değildir. Bu tür durumlarda, Julia [`MethodError`](@ref) hatasını yükseltir, rastgele bir yöntemi seçmek yerine. Yöntem belirsizliklerini, kesişim durumu için uygun bir yöntemi belirterek önleyebilirsiniz:

```jldoctest gofxy
julia> g(x::Float64, y::Float64) = 2x + 2y
g (generic function with 3 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
10.0
```

Özelleştirici yöntemin öncelikle tanımlanması önerilir, aksi takdirde belirsizlik, daha spesifik yöntem tanımlanana kadar geçici olarak var olur.

Daha karmaşık durumlarda, yöntem belirsizliklerini çözmek belirli bir tasarım unsuru içerir; bu konu daha fazla [below](@ref man-method-design-ambiguities) ile incelenmektedir.

## Parametric Methods

Yöntem tanımları, imzayı nitelendiren tür parametrelerine isteğe bağlı olarak sahip olabilir:

```jldoctest same_typefunc
julia> same_type(x::T, y::T) where {T} = true
same_type (generic function with 1 method)

julia> same_type(x,y) = false
same_type (generic function with 2 methods)
```

İlk yöntem, her iki argümanın da aynı somut türde olduğu her durumda uygulanır, bu türün ne olduğu önemli olmaksızın, ikinci yöntem ise tüm diğer durumları kapsayan bir genel yöntem olarak işlev görür. Böylece, genel olarak, iki argümanın aynı türde olup olmadığını kontrol eden bir boolean fonksiyonu tanımlanmış olur:

```jldoctest same_typefunc
julia> same_type(1, 2)
true

julia> same_type(1, 2.0)
false

julia> same_type(1.0, 2.0)
true

julia> same_type("foo", 2.0)
false

julia> same_type("foo", "bar")
true

julia> same_type(Int32(1), Int64(2))
false
```

Bu tanımlar, `UnionAll` türleri olan yöntemlere karşılık gelir (bkz. [UnionAll Types](@ref)).

Bu tür bir işlev davranışının dispatch ile tanımlanması oldukça yaygındır - hatta Julia'da idiomatik bir durumdur. Metot tür parametreleri, argümanların türleri olarak kullanılmakla sınırlı değildir: bir değerinin işlevin imzasında veya işlevin gövdesinde kullanılabileceği her yerde kullanılabilirler. İşte metot tür parametresi `T`'nin, metot imzasında parametreli tür `Vector{T}`'nin tür parametresi olarak kullanıldığı bir örnek:

```jldoctest
julia> function myappend(v::Vector{T}, x::T) where {T}
           return [v..., x]
       end
myappend (generic function with 1 method)
```

`T` tür parametresi bu örnekte eklenen `x` elemanının `v` vektörünün mevcut eleman türünün bir alt türü olmasını sağlar. `where` anahtar kelimesi, yöntem imzası tanımından sonra bu kısıtlamaların bir listesini tanıtır. Bu, yukarıda görüldüğü gibi tek satırlık tanımlar için de aynı şekilde çalışır ve mevcutsa, aşağıda gösterildiği gibi [return type declaration](@ref man-functions-return-type)'den *önce* yer almalıdır.

```jldoctest
julia> (myappend(v::Vector{T}, x::T)::Vector) where {T} = [v..., x]
myappend (generic function with 1 method)

julia> myappend([1,2,3],4)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> myappend([1,2,3],2.5)
ERROR: MethodError: no method matching myappend(::Vector{Int64}, ::Float64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]

julia> myappend([1.0,2.0,3.0],4.0)
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> myappend([1.0,2.0,3.0],4)
ERROR: MethodError: no method matching myappend(::Vector{Float64}, ::Int64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]
```

Eğer eklenen elemanın türü, eklendiği vektörün eleman türüyle eşleşmiyorsa, bir [`MethodError`](@ref) hatası oluşur. Aşağıdaki örnekte, metodun tür parametresi `T` dönüş değeri olarak kullanılır:

```jldoctest
julia> mytypeof(x::T) where {T} = T
mytypeof (generic function with 1 method)

julia> mytypeof(1)
Int64

julia> mytypeof(1.0)
Float64
```

Sadece tür bildirimlerinde tür parametreleri üzerinde alt tür kısıtlamaları koyabileceğiniz gibi (bkz. [Parametric Types](@ref)), yöntemlerin tür parametrelerini de kısıtlayabilirsiniz:

```jldoctest
julia> same_type_numeric(x::T, y::T) where {T<:Number} = true
same_type_numeric (generic function with 1 method)

julia> same_type_numeric(x::Number, y::Number) = false
same_type_numeric (generic function with 2 methods)

julia> same_type_numeric(1, 2)
true

julia> same_type_numeric(1, 2.0)
false

julia> same_type_numeric(1.0, 2.0)
true

julia> same_type_numeric("foo", 2.0)
ERROR: MethodError: no method matching same_type_numeric(::String, ::Float64)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  same_type_numeric(!Matched::T, ::T) where T<:Number
   @ Main none:1
  same_type_numeric(!Matched::Number, ::Number)
   @ Main none:1

Stacktrace:
[...]

julia> same_type_numeric("foo", "bar")
ERROR: MethodError: no method matching same_type_numeric(::String, ::String)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

julia> same_type_numeric(Int32(1), Int64(2))
false
```

`same_type_numeric` fonksiyonu, yukarıda tanımlanan `same_type` fonksiyonu gibi davranır, ancak yalnızca sayı çiftleri için tanımlanmıştır.

Parametrik yöntemler, türleri yazmak için kullanılan `where` ifadeleriyle aynı sözdizimini sağlar (bkz. [UnionAll Types](@ref)). Eğer yalnızca bir parametre varsa, dıştaki süslü parantezler ( `where {T}` içindeki) atlanabilir, ancak genellikle açıklık için tercih edilir. Birden fazla parametre virgüllerle ayrılabilir, örneğin `where {T, S<:Real}`, veya iç içe `where` kullanılarak yazılabilir, örneğin `where S<:Real where T`.

## Redefining Methods

Bir yöntemi yeniden tanımlarken veya yeni yöntemler eklerken, bu değişikliklerin hemen etkili olmayacağını anlamak önemlidir. Bu, Julia'nın kodu hızlı çalıştırmak için statik olarak çıkarım yapma ve derleme yeteneğinin anahtarıdır; bu, genellikle kullanılan JIT hileleri ve yükleri olmadan. Gerçekten de, herhangi bir yeni yöntem tanımı mevcut çalışma zamanı ortamına, Görevler ve İplikler dahil (ve daha önce tanımlanmış `@generated` işlevler) görünmeyecektir. Bunun ne anlama geldiğini görmek için bir örnekle başlayalım:

```julia-repl
julia> function tryeval()
           @eval newfun() = 1
           newfun()
       end
tryeval (generic function with 1 method)

julia> tryeval()
ERROR: MethodError: no method matching newfun()
The applicable method may be too new: running in world age xxxx1, while current world is xxxx2.
Closest candidates are:
  newfun() at none:1 (method too new to be called from this world context.)
 in tryeval() at none:1
 ...

julia> newfun()
1
```

Bu örnekte, `newfun` için yeni bir tanımın oluşturulduğunu, ancak hemen çağrılamadığını gözlemleyin. Yeni global, `tryeval` fonksiyonuna hemen görünür, bu nedenle `return newfun` (parantezsiz) yazabilirsiniz. Ancak ne siz, ne de çağıranlarınız, ne de onların çağırdığı fonksiyonlar bu yeni yöntem tanımını çağırabilir!

Ama bir istisna var: `newfun`'a *REPL'den* yapılan gelecekteki çağrılar, yeni tanımını görebilme ve çağırabilme yeteneği ile beklendiği gibi çalışır.

Ancak, `tryeval`'a yapılan gelecekteki çağrılar, `newfun`'un tanımını *REPL'deki önceki ifadede olduğu gibi* görecek ve bu nedenle `tryeval` çağrısından önceki durumu yansıtacaktır.

Kendin denemek isteyebilirsin, böylece nasıl çalıştığını görebilirsin.

Bu davranışın uygulanması bir "dünya yaşı sayacı"dır. Bu monotonik olarak artan değer, her yöntem tanım işlemini takip eder. Bu, "belirli bir çalışma zamanı ortamına görünür olan yöntem tanımlarının kümesini" tek bir sayı veya "dünya yaşı" olarak tanımlamayı sağlar. Ayrıca, iki dünyada mevcut olan yöntemleri sadece ordinal değerlerini karşılaştırarak karşılaştırmayı mümkün kılar. Yukarıdaki örnekte, `newfun` yönteminin bulunduğu "mevcut dünya"nın, `tryeval`'in çalıştırılmasına başlandığında sabitlenen görev yerel "çalışma zamanı dünyası"ndan bir fazla olduğunu görüyoruz.

Bazen bunu aşmak gerekebilir (örneğin, yukarıdaki REPL'i uyguluyorsanız). Neyse ki, kolay bir çözüm var: fonksiyonu [`Base.invokelatest`](@ref) ile çağırın:

```jldoctest
julia> function tryeval2()
           @eval newfun2() = 2
           Base.invokelatest(newfun2)
       end
tryeval2 (generic function with 1 method)

julia> tryeval2()
2
```

Sonunda, bu kuralın devreye girdiği daha karmaşık örneklere bir göz atalım. `f(x)` adında bir fonksiyon tanımlayın, başlangıçta bir yöntemi vardır:

```jldoctest redefinemethod
julia> f(x) = "original definition"
f (generic function with 1 method)
```

Başka bazı işlemler başlatın `f(x)` kullanarak:

```jldoctest redefinemethod
julia> g(x) = f(x)
g (generic function with 1 method)

julia> t = @async f(wait()); yield();
```

Şimdi `f(x)` fonksiyonuna bazı yeni yöntemler ekliyoruz:

```jldoctest redefinemethod
julia> f(x::Int) = "definition for Int"
f (generic function with 2 methods)

julia> f(x::Type{Int}) = "definition for Type{Int}"
f (generic function with 3 methods)
```

Bu sonuçların nasıl farklılık gösterdiğini karşılaştırın:

```jldoctest redefinemethod
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> fetch(schedule(t, 1))
"original definition"

julia> t = @async f(wait()); yield();

julia> fetch(schedule(t, 1))
"definition for Int"
```

## Design Patterns with Parametric Methods

Karmaşık dağıtım mantığı performans veya kullanılabilirlik için gerekli olmasa da, bazen bir algoritmayı ifade etmenin en iyi yolu olabilir. İşte bu şekilde dağıtım kullanırken bazen ortaya çıkan birkaç yaygın tasarım deseni.

### Extracting the type parameter from a super-type

İşte iyi tanımlanmış eleman türüne sahip herhangi bir `AbstractArray` alt türünün eleman türü `T`'sini döndüren doğru bir kod şablonu:

```julia
abstract type AbstractArray{T, N} end
eltype(::Type{<:AbstractArray{T}}) where {T} = T
```

üçgen yönlendirme olarak adlandırılanı kullanarak. `UnionAll` türlerinin, örneğin `eltype(AbstractArray{T} where T <: Integer)`, yukarıdaki yöntemle eşleşmediğini unutmayın. `Base` içindeki `eltype` uygulaması, bu tür durumlar için `Any`'ye bir yedek yöntem ekler.

Bir yaygın hata, eleman türünü içgörü kullanarak almaya çalışmaktır:

```julia
eltype_wrong(::Type{A}) where {A<:AbstractArray} = A.parameters[1]
```

Ancak, bunun başarısız olacağı durumları oluşturmak zor değildir:

```julia
struct BitVector <: AbstractArray{Bool, 1}; end
```

Burada hiçbir parametreye sahip olmayan bir `BitVector` türü oluşturduk, ancak eleman türü hala tamamen belirtilmiştir; `T`, `Bool` eşittir!

Başka bir hata, `supertype` kullanarak tür hiyerarşisinde yukarı doğru yürümeye çalışmaktır:

```julia
eltype_wrong(::Type{AbstractArray{T}}) where {T} = T
eltype_wrong(::Type{AbstractArray{T, N}}) where {T, N} = T
eltype_wrong(::Type{A}) where {A<:AbstractArray} = eltype_wrong(supertype(A))
```

Bu, bildirilen türler için işe yararken, üst türleri olmayan türler için başarısız olur:

```julia-repl
julia> eltype_wrong(Union{AbstractArray{Int}, AbstractArray{Float64}})
ERROR: MethodError: no method matching supertype(::Type{Union{AbstractArray{Float64,N} where N, AbstractArray{Int64,N} where N}})
Closest candidates are:
  supertype(::DataType) at operators.jl:43
  supertype(::UnionAll) at operators.jl:48
```

### Building a similar type with a different type parameter

Genel kod oluştururken, genellikle türün düzeninde bazı değişiklikler yapılmış benzer bir nesne oluşturma ihtiyacı vardır; bu da tür parametrelerinde bir değişiklik gerektirir. Örneğin, belirli bir eleman türü ile üzerinde hesaplama yapmak istediğiniz, keyfi bir eleman türüne sahip bir soyut diziye sahip olabilirsiniz. Her `AbstractArray{T}` alt türü için bu tür dönüşümünü nasıl hesaplayacağımızı tanımlayan bir yöntem uygulamalıyız. Farklı bir parametreye sahip bir alt türün başka bir alt türe genel bir dönüşümü yoktur.

`AbstractArray` alt türlerinin genellikle bunu başarmak için iki yöntem uyguladığı görülmektedir: Girdi dizisini belirli bir `AbstractArray{T, N}` soyut türünün alt türüne dönüştüren bir yöntem; ve belirli bir eleman türü ile yeni bir başlatılmamış dizi oluşturan bir yöntem. Bunların örnek uygulamaları Julia Base'te bulunabilir. İşte bunların temel bir örnek kullanımı, `input` ve `output`'un aynı türde olmasını garanti eder:

```julia
input = convert(AbstractArray{Eltype}, input)
output = similar(input, Eltype)
```

Bu uzantının bir parçası olarak, algoritmanın giriş dizisinin bir kopyasına ihtiyaç duyduğu durumlarda, [`convert`](@ref) yeterli değildir çünkü dönen değer orijinal girişi taklit edebilir. [`similar`](@ref) (çıkış dizisini oluşturmak için) ve [`copyto!`](@ref) (giriş verileriyle doldurmak için) bir giriş argümanının değiştirilebilir bir kopyası için gereksinimi ifade etmenin genel bir yoludur:

```julia
copy_with_eltype(input, Eltype) = copyto!(similar(input, Eltype), input)
```

### Iterated dispatch

Birden fazla seviyeli parametreli argüman listesini göndermek için, genellikle her bir gönderim seviyesini ayrı işlevlere ayırmak en iyisidir. Bu, tek gönderim yaklaşımına benzer bir şekilde ses çıkarabilir, ancak aşağıda göreceğimiz gibi, hala daha esnektir.

Örneğin, bir dizinin eleman türü üzerinde dağıtım yapmaya çalışmak genellikle belirsiz durumlarla karşılaşacaktır. Bunun yerine, genellikle kod, önce konteyner türü üzerinde dağıtım yapar, ardından eltype'a dayalı olarak daha spesifik bir metoda geri döner. Çoğu durumda, algoritmalar bu hiyerarşik yaklaşıma uygun bir şekilde kendilerini sunarken, diğer durumlarda bu titizlik manuel olarak çözülmelidir. Bu dağıtım dallanması, örneğin, iki matrisin toplamını hesaplama mantığında gözlemlenebilir:

```julia
# First dispatch selects the map algorithm for element-wise summation.
+(a::Matrix, b::Matrix) = map(+, a, b)
# Then dispatch handles each element and selects the appropriate
# common element type for the computation.
+(a, b) = +(promote(a, b)...)
# Once the elements have the same type, they can be added.
# For example, via primitive operations exposed by the processor.
+(a::Float64, b::Float64) = Core.add(a, b)
```

### Trait-based dispatch

Doğal bir uzantı, yukarıdaki yinelemeli dağıtımın üzerine, tür hiyerarşisi tarafından tanımlanan kümelerden bağımsız olan tür kümeleri üzerinde dağıtım yapmaya olanak tanıyan bir katman eklemektir. Böyle bir küme, söz konusu türlerin `Union`'ını yazarak oluşturulabilir, ancak bu durumda bu küme genişletilebilir olmayacaktır çünkü `Union` türleri oluşturulduktan sonra değiştirilemez. Ancak, böyle genişletilebilir bir küme, genellikle ["Holy-trait"](https://github.com/JuliaLang/julia/issues/2345#issuecomment-54537633) olarak adlandırılan bir tasarım deseni ile programlanabilir.

Bu desen, işlev argümanlarının ait olabileceği her özellik kümesi için farklı bir tekil değer (veya tür) hesaplayan genel bir işlev tanımlanarak uygulanır. Bu işlev saf ise, normal dağıtıma kıyasla performans üzerinde hiçbir etkisi yoktur.

Önceki bölümdeki örnek, [`map`](@ref) ve [`promote`](@ref)'nın uygulama detaylarını göz ardı etti; her ikisi de bu özellikler açısından çalışır. Bir matris üzerinde dönerken, `map`'in uygulanması gibi, verileri geçmek için hangi sıralamanın kullanılacağı önemli bir sorudur. `AbstractArray` alt türleri [`Base.IndexStyle`](@ref) özelliğini uyguladığında, `map` gibi diğer fonksiyonlar bu bilgiyi kullanarak en iyi algoritmayı seçebilir (bkz. [Abstract Array Interface](@ref man-interface-array)). Bu, her alt türün `map`'in özel bir versiyonunu uygulamasını gerektirmediği anlamına gelir; çünkü genel tanımlar + özellik sınıfları, sistemin en hızlı versiyonu seçmesini sağlar. İşte özellik tabanlı dağıtımı gösteren bir `map` oyuncak uygulaması:

```julia
map(f, a::AbstractArray, b::AbstractArray) = map(Base.IndexStyle(a, b), f, a, b)
# generic implementation:
map(::Base.IndexCartesian, f, a::AbstractArray, b::AbstractArray) = ...
# linear-indexing implementation (faster)
map(::Base.IndexLinear, f, a::AbstractArray, b::AbstractArray) = ...
```

Bu özellik temelli yaklaşım, skalar `+` tarafından kullanılan [`promote`](@ref) mekanizmasında da mevcuttur. Bu, iki operandın türlerine göre işlemi hesaplamak için optimal ortak türü döndüren [`promote_type`](@ref) kullanır. Bu, her tür argüman çifti için her fonksiyonu uygulama problemini, her türü ortak bir türe dönüştürme işlemi uygulama ve tercih edilen çift yönlü terfi kuralları tablosu oluşturma gibi çok daha küçük bir probleme indirgeyebilmemizi sağlar.

### Output-type computation

Özellik temelli terfi tartışması, bir matris işlemi için çıktı eleman türünü hesaplama konusundaki bir sonraki tasarım kalıbımıza geçiş sağlar.

Temel işlemleri, örneğin toplama, gerçekleştirmek için [`promote_type`](@ref) fonksiyonunu kullanarak istenen çıktı türünü hesaplarız. (Daha önce, `+` çağrısındaki `promote` çağrısında bunu iş başında görmüştük).

Daha karmaşık matris fonksiyonları için, daha karmaşık bir işlem dizisi için beklenen dönüş türünü hesaplamak gerekebilir. Bu genellikle aşağıdaki adımlarla gerçekleştirilir:

1. Write a small function `op` that expresses the set of operations performed by the kernel of the algorithm.
2. Sonuç matrisinin eleman tipini `promote_op(op, argument_types...)` olarak hesaplayın; burada `argument_types`, her bir girdi dizisine uygulanan `eltype` ile hesaplanır.
3. `similar(R, dims)` fonksiyonu ile çıktı matrisini oluşturun; burada `dims`, çıktı dizisinin istenen boyutlarıdır.

Daha spesifik bir örnek için, genel bir kare matris çarpma sahte kodu şöyle görünebilir:

```julia
function matmul(a::AbstractMatrix, b::AbstractMatrix)
    op = (ai, bi) -> ai * bi + ai * bi

    ## this is insufficient because it assumes `one(eltype(a))` is constructable:
    # R = typeof(op(one(eltype(a)), one(eltype(b))))

    ## this fails because it assumes `a[1]` exists and is representative of all elements of the array
    # R = typeof(op(a[1], b[1]))

    ## this is incorrect because it assumes that `+` calls `promote_type`
    ## but this is not true for some types, such as Bool:
    # R = promote_type(ai, bi)

    # this is wrong, since depending on the return value
    # of type-inference is very brittle (as well as not being optimizable):
    # R = Base.return_types(op, (eltype(a), eltype(b)))

    ## but, finally, this works:
    R = promote_op(op, eltype(a), eltype(b))
    ## although sometimes it may give a larger type than desired
    ## it will always give a correct type

    output = similar(b, R, (size(a, 1), size(b, 2)))
    if size(a, 2) > 0
        for j in 1:size(b, 2)
            for i in 1:size(a, 1)
                ## here we don't use `ab = zero(R)`,
                ## since `R` might be `Any` and `zero(Any)` is not defined
                ## we also must declare `ab::R` to make the type of `ab` constant in the loop,
                ## since it is possible that typeof(a * b) != typeof(a * b + a * b) == R
                ab::R = a[i, 1] * b[1, j]
                for k in 2:size(a, 2)
                    ab += a[i, k] * b[k, j]
                end
                output[i, j] = ab
            end
        end
    end
    return output
end
```

### Separate convert and kernel logic

Bir yolu, derleme sürelerini ve test karmaşıklığını önemli ölçüde azaltmak, istenen türe dönüştürme mantığını ve hesaplamayı izole etmektir. Bu, derleyicinin dönüşüm mantığını, daha büyük çekirdeğin geri kalanından bağımsız olarak özelleştirmesine ve içermesine olanak tanır.

Bu, bir algoritmanın gerçekten desteklediği belirli bir argüman türüne daha büyük bir türler sınıfından dönüşüm yaparken görülen yaygın bir kalıptır:

```julia
complexfunction(arg::Int) = ...
complexfunction(arg::Any) = complexfunction(convert(Int, arg))

matmul(a::T, b::T) = ...
matmul(a, b) = matmul(promote(a, b)...)
```

## Parametrically-constrained Varargs methods

Fonksiyon parametreleri, bir "varargs" fonksiyonuna sağlanabilecek argüman sayısını kısıtlamak için de kullanılabilir ([Varargs Functions](@ref)). Böyle bir kısıtlamayı belirtmek için `Vararg{T,N}` notasyonu kullanılır. Örneğin:

```jldoctest
julia> bar(a,b,x::Vararg{Any,2}) = (a,b,x)
bar (generic function with 1 method)

julia> bar(1,2,3)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, !Matched::Any)
   @ Main none:1

Stacktrace:
[...]

julia> bar(1,2,3,4)
(1, 2, (3, 4))

julia> bar(1,2,3,4,5)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Daha faydalı bir şekilde, varargs yöntemlerini bir parametre ile kısıtlamak mümkündür. Örneğin:

```julia
function getindex(A::AbstractArray{T,N}, indices::Vararg{Number,N}) where {T,N}
```

sadece `indices` sayısı dizinin boyutuyla eşleştiğinde çağrılacaktır.

Sadece sağlanan argümanların türü kısıtlandığında `Vararg{T}` eşdeğer olarak `T...` şeklinde yazılabilir. Örneğin `f(x::Int...) = x`, `f(x::Vararg{Int}) = x` için bir kısayoldur.

## Note on Optional and keyword Arguments

Belirtilen [Functions](@ref man-functions) içinde kısaca bahsedildiği gibi, isteğe bağlı argümanlar birden fazla yöntem tanımı için sözdizimi olarak uygulanmaktadır. Örneğin, bu tanım:

```julia
f(a=1,b=2) = a+2b
```

aşağıdaki üç yönteme çevirir:

```julia
f(a,b) = a+2b
f(a) = f(a,2)
f() = f(1,2)
```

Bu, `f()` çağırmanın `f(1,2)` çağırmaya eşdeğer olduğu anlamına gelir. Bu durumda sonuç `5`'tir, çünkü `f(1,2)` yukarıdaki `f`'nin ilk yöntemini çağırır. Ancak, bu her zaman böyle olmak zorunda değildir. Eğer tam sayılar için daha özel bir dördüncü yöntem tanımlarsanız:

```julia
f(a::Int,b::Int) = a-2b
```

sonuç olarak hem `f()` hem de `f(1,2)` `-3` değerini döndürür. Diğer bir deyişle, isteğe bağlı argümanlar bir işlevle ilişkilidir, o işlevin herhangi bir belirli yöntemiyle değil. Hangi yöntemin çağrılacağı, isteğe bağlı argümanların türlerine bağlıdır. İsteğe bağlı argümanlar bir global değişkenle tanımlandığında, isteğe bağlı argümanın türü çalışma zamanında bile değişebilir.

Anahtar argümanlar, sıradan konum argümanlarından oldukça farklı davranır. Özellikle, yöntem dağıtımında yer almazlar. Yöntemler yalnızca konum argümanlarına dayalı olarak dağıtılır ve anahtar argümanlar, eşleşen yöntem belirlendikten sonra işlenir.

## Function-like objects

Yöntemler türlerle ilişkilidir, bu nedenle herhangi bir keyfi Julia nesnesini "çağrılabilir" hale getirmek için türüne yöntemler eklemek mümkündür. (Bu tür "çağrılabilir" nesnelere bazen "fonktörler" denir.)

Örneğin, bir polinomun katsayılarını saklayan ancak polinomu değerlendiren bir fonksiyon gibi davranan bir tür tanımlayabilirsiniz:

```jldoctest polynomial
julia> struct Polynomial{R}
           coeffs::Vector{R}
       end

julia> function (p::Polynomial)(x)
           v = p.coeffs[end]
           for i = (length(p.coeffs)-1):-1:1
               v = v*x + p.coeffs[i]
           end
           return v
       end

julia> (p::Polynomial)() = p(5)
```

Fonksiyonun ad yerine tür ile belirtildiğini unutmayın. Normal fonksiyonlarda olduğu gibi kısa bir sözdizimi biçimi vardır. Fonksiyon gövdesinde, `p` çağrılan nesneye atıfta bulunacaktır. Bir `Polynomial` aşağıdaki gibi kullanılabilir:

```jldoctest polynomial
julia> p = Polynomial([1,10,100])
Polynomial{Int64}([1, 10, 100])

julia> p(3)
931

julia> p()
2551
```

Bu mekanizma, Julia'da tür yapıcılarının ve çevrelerini referans alan kapalı fonksiyonların (iç fonksiyonlar) nasıl çalıştığının anahtarıdır.

## Empty generic functions

Bazen, henüz yöntem eklemeden genel bir işlev tanıtmak faydalı olabilir. Bu, arayüz tanımlarını uygulamalardan ayırmak için kullanılabilir. Ayrıca, belgeleme veya kod okunabilirliği amacıyla da yapılabilir. Bunun için sözdizimi, bir argüman demeti olmadan boş bir `function` bloğudur:

```julia
function emptyfunc end
```

## [Method design and the avoidance of ambiguities](@id man-method-design-ambiguities)

Julia'nın yöntem çok biçimliliği, en güçlü özelliklerinden biridir, ancak bu gücü kullanmak tasarım zorlukları yaratabilir. Özellikle, daha karmaşık yöntem hiyerarşilerinde [ambiguities](@ref man-ambiguities)'in ortaya çıkması yaygındır.

Yukarıda, belirsizliklerin nasıl çözülebileceği belirtildi.

```julia
f(x, y::Int) = 1
f(x::Int, y) = 2
```

bir yöntem tanımlayarak

```julia
f(x::Int, y::Int) = 3
```

Bu genellikle doğru bir stratejidir; ancak, bu tavsiyeyi düşünmeden takip etmenin ters etki yaratabileceği durumlar vardır. Özellikle, bir genel işlevin sahip olduğu yöntem sayısı arttıkça, belirsizlikler için daha fazla olasılık ortaya çıkar. Yöntem hiyerarşileriniz bu basit örnekten daha karmaşık hale geldiğinde, alternatif stratejiler hakkında dikkatlice düşünmek zamanınızı değerli kılabilir.

Aşağıda belirli zorlukları ve bu tür sorunları çözmek için bazı alternatif yolları tartışıyoruz.

### Tuple and NTuple arguments

`Tuple` (ve `NTuple`) argümanları özel zorluklar sunar. Örneğin,

```julia
f(x::NTuple{N,Int}) where {N} = 1
f(x::NTuple{N,Float64}) where {N} = 2
```

belirsizdir çünkü `N == 0` olasılığı vardır: `Int` veya `Float64` varyantının çağrılıp çağrılmayacağını belirlemek için hiçbir eleman yoktur. Belirsizliği çözmek için bir yaklaşım, boş demet için bir yöntem tanımlamaktır:

```julia
f(x::Tuple{}) = 3
```

Alternatif olarak, bir yöntem hariç tüm yöntemler için, tuple içinde en az bir öğe olduğunu ısrarla belirtebilirsiniz:

```julia
f(x::NTuple{N,Int}) where {N} = 1           # this is the fallback
f(x::Tuple{Float64, Vararg{Float64}}) = 2   # this requires at least one Float64
```

### [Orthogonalize your design](@id man-methods-orthogonalize)

İki veya daha fazla argümanla gönderim yapma konusunda cazip hale geldiğinizde, bir "sarmalayıcı" fonksiyonun daha basit bir tasarım sunup sunmayacağını düşünün. Örneğin, birden fazla varyant yazmak yerine:

```julia
f(x::A, y::A) = ...
f(x::A, y::B) = ...
f(x::B, y::A) = ...
f(x::B, y::B) = ...
```

bunu tanımlamayı düşünebilirsiniz

```julia
f(x::A, y::A) = ...
f(x, y) = f(g(x), g(y))
```

burada `g` argümanı `A` türüne dönüştürür. Bu, [orthogonal design](https://en.wikipedia.org/wiki/Orthogonality_(programming)) daha genel ilkesinin çok özel bir örneğidir; burada ayrı kavramlar ayrı yöntemlere atanır. Burada, `g` muhtemelen bir yedek tanıma ihtiyaç duyacaktır.

```julia
g(x::A) = x
```

İlgili bir strateji, `promote` kullanarak `x` ve `y`'yi ortak bir türe getirmektedir:

```julia
f(x::T, y::T) where {T} = ...
f(x, y) = f(promote(x, y)...)
```

Bu tasarımla ilgili bir risk, `x` ve `y`'yi aynı türe dönüştüren uygun bir tanıtım yöntemi yoksa, ikinci yöntemin kendisi üzerinde sonsuz bir şekilde yineleme yapması ve bir yığın taşması tetiklemesidir.

### Dispatch on one argument at a time

Eğer birden fazla argüman üzerinde dağıtım yapmanız gerekiyorsa ve çok fazla kombinasyonla birlikte çok fazla yedek varsa, tüm olası varyantları tanımlamanın pratik olmadığını düşünüyorsanız, "isim kaskadı" tanıtmayı düşünün; burada (örneğin) ilk argüman üzerinde dağıtım yapar ve ardından bir iç yöntemi çağırırsınız:

```julia
f(x::A, y) = _fA(x, y)
f(x::B, y) = _fB(x, y)
```

O zaman iç yöntemler `_fA` ve `_fB`, `x` ile ilgili olarak birbirleriyle çelişme endişesi olmadan `y` üzerinde yönlendirme yapabilir.

Bu stratejinin en az bir büyük dezavantajı olduğunu unutmayın: birçok durumda, kullanıcıların `f` fonksiyonunuzun davranışını daha fazla özelleştirmesi mümkün değildir. Bunun yerine, iç yöntemleriniz olan `_fA` ve `_fB` için özelleştirmeler tanımlamak zorundadırlar ve bu, dışa aktarılan ve iç yöntemler arasındaki sınırları bulanıklaştırır.

### Abstract containers and element types

Mümkünse, soyut konteynerlerin belirli eleman türlerine göre dağıtım yapan yöntemler tanımlamaktan kaçının. Örneğin,

```julia
-(A::AbstractArray{T}, b::Date) where {T<:Date}
```

herhangi bir yöntemi tanımlayan herkes için belirsizlikler oluşturur

```julia
-(A::MyArrayType{T}, b::T) where {T}
```

En iyi yaklaşım, bu yöntemlerin *herhangi birini* tanımlamaktan kaçınmaktır: bunun yerine, `-(A::AbstractArray, b)` adlı genel bir yönteme güvenin ve bu yöntemin her konteyner türü ve eleman türü için *ayrı ayrı* doğru şeyi yapan genel çağrılar (gibi `similar` ve `-`) ile uygulandığından emin olun. Bu, yöntemlerinizi [orthogonalize](@ref man-methods-orthogonalize) tavsiyesinin daha karmaşık bir varyasyonudur.

Bu yaklaşım mümkün olmadığında, belirsizliği çözmek için diğer geliştiricilerle bir tartışma başlatmak faydalı olabilir; bir yöntem ilk olarak tanımlandı diye, bunun değiştirilmesi veya ortadan kaldırılması mümkün değildir anlamına gelmez. Son çare olarak, bir geliştirici "bandaj" yöntemini tanımlayabilir.

```julia
-(A::MyArrayType{T}, b::Date) where {T<:Date} = ...
```

bu zorla belirsizliği çözer.

### Complex method "cascades" with default arguments

Eğer varsayılanları sağlayan "cascade" adında bir yöntem tanımlıyorsanız, potansiyel varsayılanlara karşılık gelen herhangi bir argümanı düşürmekten dikkatli olun. Örneğin, bir dijital filtreleme algoritması yazıyorsanız ve sinyalin kenarlarını yastıklama uygulayarak işleyen bir yönteminiz varsa:

```julia
function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel)  # now perform the "real" computation
end
```

Bu, varsayılan dolgu sağlayan bir yöntemle çelişecektir:

```julia
myfilter(A, kernel) = myfilter(A, kernel, Replicate()) # replicate the edge by default
```

Birlikte, bu iki yöntem `A`'nın sürekli büyüdüğü sonsuz bir özyineleme oluşturur.

Daha iyi bir tasarım, çağrı hiyerarşinizi şu şekilde tanımlamak olacaktır:

```julia
struct NoPad end  # indicate that no padding is desired, or that it's already applied

myfilter(A, kernel) = myfilter(A, kernel, Replicate())  # default boundary conditions

function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel, NoPad())  # indicate the new boundary conditions
end

# other padding methods go here

function myfilter(A, kernel, ::NoPad)
    # Here's the "real" implementation of the core computation
end
```

`NoPad`, diğer her türlü dolgu ile aynı argüman konumunda sağlandığı için, dağıtım hiyerarşisini iyi organize eder ve belirsizlik olasılığını azaltır. Ayrıca, "kamusal" `myfilter` arayüzünü genişletir: dolgu kontrolünü açıkça yapmak isteyen bir kullanıcı, `NoPad` varyantını doğrudan çağırabilir.

## Defining methods in local scope

Bir [local scope](@ref scope-of-variables) içinde yöntemler tanımlayabilirsiniz, örneğin

```jldoctest
julia> function f(x)
           g(y::Int) = y + x
           g(y) = y - x
           g
       end
f (generic function with 1 method)

julia> h = f(3);

julia> h(4)
7

julia> h(4.0)
1.0
```

Ancak, yerel yöntemleri koşullu olarak veya kontrol akışına tabi olarak tanımlamamalısınız, şöyle ki

```julia
function f2(inc)
    if inc
        g(x) = x + 1
    else
        g(x) = x - 1
    end
end

function f3()
    function g end
    return g
    g() = 0
end
```

belirli bir işlevin nasıl tanımlanacağı net olmadığı için. Gelecekte, yerel yöntemleri bu şekilde tanımlamak bir hata olabilir.

Bunun gibi durumlar için anonim fonksiyonlar kullanın:

```julia
function f2(inc)
    g = if inc
        x -> x + 1
    else
        x -> x - 1
    end
end
```

[^Clarke61]: Arthur C. Clarke, *Profiles of the Future* (1961): Clarke's Third Law.
