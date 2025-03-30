Lockable(value, lock = ReentrantLock())

`value` ile birlikte sağlanan `lock` ile ilişkilendirilmiş bir `Lockable` nesnesi oluşturur. Bu nesne [`@lock`](@ref), [`lock`](@ref), [`trylock`](@ref), [`unlock`](@ref) destekler. Değere erişmek için, kilidi tutarken kilitlenebilir nesneyi indeksleyin.

!!! compat "Julia 1.11"
    En az Julia 1.11 gerektirir.


## Örnek

```jldoctest
julia> locked_list = Base.Lockable(Int[]);

julia> @lock(locked_list, push!(locked_list[], 1)) # değere erişmek için kilidi tutmalısınız
1-element Vector{Int64}:
 1

julia> lock(summary, locked_list)
"1-element Vector{Int64}"
```
