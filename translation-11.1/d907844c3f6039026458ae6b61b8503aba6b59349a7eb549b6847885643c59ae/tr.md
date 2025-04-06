```
NamedTuple
```

`NamedTuple`lar, adından da anlaşılacağı gibi, adlandırılmış [`Tuple`](@ref)lar. Yani, her bir girişin benzersiz bir adı olduğu, değerlerin tuple benzeri bir koleksiyonu; bu adlar [`Symbol`](@ref) olarak temsil edilir. `Tuple`lar gibi, `NamedTuple`lar da değiştirilemez; inşa edildikten sonra ne adlar ne de değerler yerinde değiştirilemez.

Adlandırılmış bir tuple, anahtarlarla bir tuple literal olarak oluşturulabilir, örneğin `(a=1, b=2)`, veya açılış parantezinden sonra noktalı virgül ile bir tuple literal olarak, örneğin `(; a=1, b=2)` (bu form ayrıca aşağıda açıklanan programatik olarak üretilen adları da kabul eder), veya bir `NamedTuple` türü kullanılarak bir yapıcı olarak, örneğin `NamedTuple{(:a, :b)}((1,2))`.

Adlandırılmış bir tuple'daki bir adla ilişkili değere erişim, alan erişim sözdizimi kullanılarak yapılabilir, örneğin `x.a`, veya [`getindex`](@ref) kullanılarak, örneğin `x[:a]` veya `x[(:a, :b)]`. Adların bir tuple'ı [`keys`](@ref) kullanılarak elde edilebilir ve değerlerin bir tuple'ı [`values`](@ref) kullanılarak elde edilebilir.

!!! note
    `NamedTuple`lar üzerinde yineleme, adlar olmadan *değerleri* üretir. (Aşağıdaki örneğe bakın.) Ad-değer çiftleri üzerinde yineleme yapmak için [`pairs`](@ref) fonksiyonunu kullanın.


[`@NamedTuple`](@ref) makrosu, `NamedTuple` türlerini rahatça tanımlamak için kullanılabilir.

# Örnekler

```jldoctest
julia> x = (a=1, b=2)
(a = 1, b = 2)

julia> x.a
1

julia> x[:a]
1

julia> x[(:a,)]
(a = 1,)

julia> keys(x)
(:a, :b)

julia> values(x)
(1, 2)

julia> collect(x)
2-element Vector{Int64}:
 1
 2

julia> collect(pairs(x))
2-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
```

Anahtar argümanları programatik olarak tanımlama şekline benzer bir şekilde, bir adlandırılmış tuple, bir tuple literal içinde noktalı virgülden sonra `name::Symbol => value` çiftleri vererek oluşturulabilir. Bu ve `name=value` sözdizimi karıştırılabilir:

```jldoctest
julia> (; :a => 1, :b => 2, c=3)
(a = 1, b = 2, c = 3)
```

Ad-değer çiftleri, bir adlandırılmış tuple'ı veya her biri bir sembolü ilk değer olarak tutan iki değerli koleksiyonlar üreten herhangi bir yineleyiciyi açarak da sağlanabilir:

```jldoctest
julia> keys = (:a, :b, :c); values = (1, 2, 3);

julia> NamedTuple{keys}(values)
(a = 1, b = 2, c = 3)

julia> (; (keys .=> values)...)
(a = 1, b = 2, c = 3)

julia> nt1 = (a=1, b=2);

julia> nt2 = (c=3, d=4);

julia> (; nt1..., nt2..., b=20) # son b, nt1'den gelen değeri geçersiz kılar
(a = 1, b = 20, c = 3, d = 4)

julia> (; zip(keys, values)...) # zip, (:a, 1) gibi tuple'lar üretir
(a = 1, b = 2, c = 3)
```

Anahtar argümanlarda olduğu gibi, tanımlayıcılar ve nokta ifadeleri adları ima eder:

```jldoctest
julia> x = 0
0

julia> t = (; x)
(x = 0,)

julia> (; t.x)
(x = 0,)
```

!!! compat "Julia 1.5"
    Tanımlayıcılardan ve nokta ifadelerinden gelen örtük adlar, Julia 1.5 itibarıyla mevcuttur.


!!! compat "Julia 1.7"
    Birden fazla `Symbol` ile `getindex` yöntemlerinin kullanımı, Julia 1.7 itibarıyla mevcuttur.

