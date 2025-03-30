```
@allocations
```

Bir ifadeyi değerlendirmek, elde edilen değeri atmak ve bunun yerine ifadenin değerlendirilmesi sırasında toplam tahsis sayısını döndürmek için bir makro.

Ayrıca bkz. [`@allocated`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref) ve [`@elapsed`](@ref).

```julia-repl
julia> @allocations rand(10^6)
2
```

!!! compat "Julia 1.9"
    Bu makro Julia 1.9'da eklendi.

