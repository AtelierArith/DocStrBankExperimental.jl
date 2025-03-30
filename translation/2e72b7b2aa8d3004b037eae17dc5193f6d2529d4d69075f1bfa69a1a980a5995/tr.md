```
all(itr) -> Bool
```

Bir boolean koleksiyonundaki tüm elemanların `true` olup olmadığını test eder, `itr` içinde ilk `false` değeri ile karşılaşıldığında `false` döner (kısa devre). `true` üzerinde kısa devre yapmak için [`any`](@ref) kullanın.

Girdi [`missing`](@ref) değerleri içeriyorsa, tüm eksik olmayan değerler `true` ise (veya eşdeğer olarak, girdi `false` değeri içermiyorsa) `missing` döner, [üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) izlenir.

Ayrıca bakınız: [`all!`](@ref), [`any`](@ref), [`count`](@ref), [`&`](@ref), , [`&&`](@ref), [`allunique`](@ref).

# Örnekler

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> all(a)
false

julia> all((println(i); v) for (i, v) in enumerate(a))
1
2
false

julia> all([missing, false])
false

julia> all([true, missing])
missing
```
