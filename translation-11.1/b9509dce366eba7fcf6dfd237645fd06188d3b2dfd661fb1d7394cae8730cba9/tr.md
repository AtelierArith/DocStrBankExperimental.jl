```
any(itr) -> Bool
```

Bir boolean koleksiyonundaki herhangi bir elemanın `true` olup olmadığını test eder, `itr` içinde ilk `true` değeri bulunduğunda `true` döner (kısa devre). `false` üzerinde kısa devre yapmak için [`all`](@ref) kullanın.

Girdi [`missing`](@ref) değerleri içeriyorsa, tüm eksik olmayan değerler `false` ise (veya eşdeğer olarak, girdi `true` değeri içermiyorsa) `missing` döner, [üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) izlenir.

Ayrıca bakınız: [`all`](@ref), [`count`](@ref), [`sum`](@ref), [`|`](@ref), , [`||`](@ref).

# Örnekler

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> any(a)
true

julia> any((println(i); v) for (i, v) in enumerate(a))
1
true

julia> any([missing, true])
true

julia> any([false, missing])
missing
```
