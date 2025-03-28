```
Threads.atomic_add!(x::Atomic{T}, val::T) donde T <: ArithmeticTypes
```

Suma `val` a `x` de manera atómica

Realiza `x[] += val` de manera atómica. Devuelve el **valor** **antiguo**. No está definido para `Atomic{Bool}`.

Para más detalles, consulta la instrucción `atomicrmw add` de LLVM.

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_add!(x, 2)
3

julia> x[]
5
```
