Lockable(value, lock = ReentrantLock())

Erstellt ein `Lockable`-Objekt, das `value` umschließt und es mit dem bereitgestellten `lock` verknüpft. Dieses Objekt unterstützt [`@lock`](@ref), [`lock`](@ref), [`trylock`](@ref), [`unlock`](@ref). Um auf den Wert zuzugreifen, indizieren Sie das lockable Objekt, während Sie den Lock halten.

!!! compat "Julia 1.11"
    Erfordert mindestens Julia 1.11.


## Beispiel

```jldoctest
julia> locked_list = Base.Lockable(Int[]);

julia> @lock(locked_list, push!(locked_list[], 1)) # muss den Lock halten, um auf den Wert zuzugreifen
1-element Vector{Int64}:
 1

julia> lock(summary, locked_list)
"1-element Vector{Int64}"
```
