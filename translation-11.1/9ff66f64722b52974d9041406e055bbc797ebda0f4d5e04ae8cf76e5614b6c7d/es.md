Lockable(value, lock = ReentrantLock())

Crea un objeto `Lockable` que envuelve `value` y lo asocia con el `lock` proporcionado. Este objeto soporta [`@lock`](@ref), [`lock`](@ref), [`trylock`](@ref), [`unlock`](@ref). Para acceder al valor, indexa el objeto bloqueable mientras sostienes el bloqueo.

!!! compat "Julia 1.11"
    Requiere al menos Julia 1.11.


## Ejemplo

```jldoctest
julia> locked_list = Base.Lockable(Int[]);

julia> @lock(locked_list, push!(locked_list[], 1)) # debes sostener el bloqueo para acceder al valor
1-element Vector{Int64}:
 1

julia> lock(summary, locked_list)
"1-element Vector{Int64}"
```
