```
begin
```

`begin...end` denota un bloque de código.

```julia
begin
    println("Hola, ")
    println("¡Mundo!")
end
```

Usualmente `begin` no será necesario, ya que palabras clave como [`function`](@ref) y [`let`](@ref) comienzan implícitamente bloques de código. Ver también [`;`](@ref).

`begin` también puede ser utilizado al indexar para representar el primer índice de una colección o el primer índice de una dimensión de un arreglo. Por ejemplo, `a[begin]` es el primer elemento de un arreglo `a`.

!!! compat "Julia 1.4"
    El uso de `begin` como un índice requiere Julia 1.4 o posterior.


# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64,2}:
 1  2
 3  4

julia> A[begin, :]
2-element Array{Int64,1}:
 1
 2
```
