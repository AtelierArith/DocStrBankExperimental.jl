```
zip(iters...)
```

Birden fazla iteratörü aynı anda çalıştırır, bunlardan herhangi biri tükenene kadar. `zip` iteratörünün değer türü, alt iteratörlerinin değerlerinin bir demetidir.

!!! note
    `zip`, alt iteratörlerine yapılan çağrıları, durum bilgisi olan iteratörlerin mevcut yinelemede başka bir iteratör bittiğinde ilerlemeyeceği şekilde düzenler.


!!! note
    `zip()` argüman olmadan, boş demetlerden oluşan sonsuz bir iteratör üretir.


Ayrıca bakınız: [`enumerate`](@ref), [`Base.splat`](@ref).

# Örnekler

```jldoctest
julia> a = 1:5
1:5

julia> b = ["e","d","b","c","a"]
5-element Vector{String}:
 "e"
 "d"
 "b"
 "c"
 "a"

julia> c = zip(a,b)
zip(1:5, ["e", "d", "b", "c", "a"])

julia> length(c)
5

julia> first(c)
(1, "e")
```
