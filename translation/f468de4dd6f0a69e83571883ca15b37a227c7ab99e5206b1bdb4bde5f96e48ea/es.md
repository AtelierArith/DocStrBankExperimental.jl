```
Threads.Atomic{T}
```

Mantiene una referencia a un objeto del tipo `T`, asegurando que solo se acceda a él de manera atómica, es decir, de forma segura para hilos.

Solo ciertos tipos "simples" pueden usarse de manera atómica, a saber, los tipos primitivos booleanos, enteros y de punto flotante. Estos son `Bool`, `Int8`...`Int128`, `UInt8`...`UInt128`, y `Float16`...`Float64`.

Se pueden crear nuevos objetos atómicos a partir de valores no atómicos; si no se especifica ninguno, el objeto atómico se inicializa con cero.

Los objetos atómicos se pueden acceder utilizando la notación `[]`:

# Ejemplos

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> x[] = 1
1

julia> x[]
1
```

Las operaciones atómicas utilizan un prefijo `atomic_`, como [`atomic_add!`](@ref), [`atomic_xchg!`](@ref), etc.
