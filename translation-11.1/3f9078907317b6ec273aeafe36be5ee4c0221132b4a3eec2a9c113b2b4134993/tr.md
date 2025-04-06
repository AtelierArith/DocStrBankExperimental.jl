```
@allocated
```

Bir ifadeyi değerlendirmek için kullanılan bir makro, sonuç değerini atarak, bunun yerine ifadenin değerlendirilmesi sırasında tahsis edilen toplam byte sayısını döndürür.

Ayrıca [`@allocations`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref) ve [`@elapsed`](@ref) ile de bakınız.

```julia-repl
julia> @allocated rand(10^6)
8000080
```
