```
Threads.atomic_cas!(x::Atomic{T}, cmp::T, newval::T) where T
```

Compara y establece `x` de manera atómica

Compara de manera atómica el valor en `x` con `cmp`. Si son iguales, escribe `newval` en `x`. De lo contrario, deja `x` sin modificar. Devuelve el valor antiguo en `x`. Al comparar el valor devuelto con `cmp` (a través de `===`), se sabe si `x` fue modificado y ahora tiene el nuevo valor `newval`.

Para más detalles, consulta la instrucción `cmpxchg` de LLVM.

Esta función se puede utilizar para implementar semánticas transaccionales. Antes de la transacción, se registra el valor en `x`. Después de la transacción, el nuevo valor se almacena solo si `x` no ha sido modificado en el ínterin.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 4, 2);

julia> x
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_cas!(x, 3, 2);

julia> x
Base.Threads.Atomic{Int64}(2)
```
