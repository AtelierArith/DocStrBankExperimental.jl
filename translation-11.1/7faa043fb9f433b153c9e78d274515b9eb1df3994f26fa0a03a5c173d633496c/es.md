```
Iterators.accumulate(f, itr; [init])
```

Dada una función de 2 argumentos `f` y un iterador `itr`, devuelve un nuevo iterador que aplica sucesivamente `f` al valor anterior y al siguiente elemento de `itr`.

Esto es efectivamente una versión perezosa de [`Base.accumulate`](@ref).

!!! compat "Julia 1.5"
    El argumento clave `init` se agregó en Julia 1.5.


# Ejemplos

```jldoctest
julia> a = Iterators.accumulate(+, [1,2,3,4]);

julia> foreach(println, a)
1
3
6
10

julia> b = Iterators.accumulate(/, (2, 5, 2, 5); init = 100);

julia> collect(b)
4-element Vector{Float64}:
 50.0
 10.0
  5.0
  1.0
```
