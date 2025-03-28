```
f ∘ g
```

Componer funciones: es decir, `(f ∘ g)(args...; kwargs...)` significa `f(g(args...; kwargs...))`. El símbolo `∘` se puede ingresar en el REPL de Julia (y en la mayoría de los editores, configurados adecuadamente) escribiendo `\circ<tab>`.

La composición de funciones también funciona en forma de prefijo: `∘(f, g)` es lo mismo que `f ∘ g`. La forma de prefijo admite la composición de múltiples funciones: `∘(f, g, h) = f ∘ g ∘ h` y el splatting `∘(fs...)` para componer una colección iterable de funciones. El último argumento de `∘` se ejecuta primero.

!!! compat "Julia 1.4"
    La composición de múltiples funciones requiere al menos Julia 1.4.


!!! compat "Julia 1.5"
    La composición de una función ∘(f) requiere al menos Julia 1.5.


!!! compat "Julia 1.7"
    El uso de argumentos de palabra clave requiere al menos Julia 1.7.


# Ejemplos

```jldoctest
julia> map(uppercase∘first, ["apple", "banana", "carrot"])
3-element Vector{Char}:
 'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)
 'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
 'C': ASCII/Unicode U+0043 (category Lu: Letter, uppercase)

julia> (==(6)∘length).(["apple", "banana", "carrot"])
3-element BitVector:
 0
 1
 1

julia> fs = [
           x -> 2x
           x -> x-1
           x -> x/2
           x -> x+1
       ];

julia> ∘(fs...)(3)
2.0
```

Ver también [`ComposedFunction`](@ref), [`!f::Function`](@ref).
