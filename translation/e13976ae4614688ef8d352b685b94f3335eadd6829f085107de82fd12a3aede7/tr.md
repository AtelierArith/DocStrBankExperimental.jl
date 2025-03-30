```
oneunit(x::T)
oneunit(T::Type)
```

`T(one(x))` döndürür, burada `T` ya argümanın türü ya da (bir tür geçerse) argümandır. Bu, boyutlu nicelikler için [`one`](@ref) ile farklıdır: `one` boyutsuzdur (çarpan kimliği) iken `oneunit` boyutludur (aynı türde `x` ile ya da `T` türünde).

# Örnekler

```jldoctest
julia> oneunit(3.7)
1.0

julia> import Dates; oneunit(Dates.Day)
1 gün
```
