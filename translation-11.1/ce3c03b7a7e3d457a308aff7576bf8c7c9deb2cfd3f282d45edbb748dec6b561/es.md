```
@boundscheck(blk)
```

Anota la expresión `blk` como un bloque de verificación de límites, permitiendo que sea elidido por [`@inbounds`](@ref).

!!! note
    La función en la que se escribe `@boundscheck` debe ser inlined en su llamador para que `@inbounds` tenga efecto.


# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> @inline function g(A, i)
           @boundscheck checkbounds(A, i)
           return "accediendo ($A)[$i]"
       end;

julia> f1() = return g(1:2, -1);

julia> f2() = @inbounds return g(1:2, -1);

julia> f1()
ERROR: BoundsError: intento de acceder a UnitRange{Int64} de 2 elementos en el índice [-1]
Stacktrace:
 [1] throw_boundserror(::UnitRange{Int64}, ::Tuple{Int64}) at ./abstractarray.jl:455
 [2] checkbounds at ./abstractarray.jl:420 [inlined]
 [3] g at ./none:2 [inlined]
 [4] f1() at ./none:1
 [5] top-level scope

julia> f2()
"accediendo (1:2)[-1]"
```

!!! warning
    La anotación `@boundscheck` te permite, como escritor de bibliotecas, optar por permitir que *otro código* elimine tus verificaciones de límites con [`@inbounds`](@ref). Como se mencionó allí, el llamador debe verificar—usando información a la que pueden acceder—que sus accesos son válidos antes de usar `@inbounds`. Por ejemplo, para indexar en tus subclases de [`AbstractArray`](@ref), esto implica verificar los índices contra sus [`axes`](@ref). Por lo tanto, las anotaciones `@boundscheck` solo deben añadirse a una implementación de [`getindex`](@ref) o [`setindex!`](@ref) después de que estés seguro de que su comportamiento es correcto.

