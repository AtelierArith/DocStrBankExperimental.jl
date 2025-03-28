```
rand([rng=default_rng()], [S], [dims...])
```

Elige un elemento aleatorio o un arreglo de elementos aleatorios del conjunto de valores especificado por `S`; `S` puede ser

  * una colección indexable (por ejemplo `1:9` o `('x', "y", :z)`)
  * un objeto `AbstractDict` o `AbstractSet`
  * una cadena (considerada como una colección de caracteres), o
  * un tipo de la lista a continuación, correspondiente al conjunto de valores especificado

      * tipos de enteros concretos muestrean de `typemin(S):typemax(S)` (excepto [`BigInt`](@ref) que no es compatible)
      * tipos de punto flotante concretos muestrean de `[0, 1)`
      * tipos complejos concretos `Complex{T}` si `T` es un tipo muestreable toman sus componentes reales e imaginarias independientemente del conjunto de valores correspondiente a `T`, pero no son compatibles si `T` no es muestreable.
      * todos los tipos `<:AbstractChar` muestrean del conjunto de escalares Unicode válidos
      * un tipo definido por el usuario y conjunto de valores; para orientación sobre la implementación, consulte [Hooking into the `Random` API](@ref rand-api-hook)
      * un tipo de tupla de tamaño conocido y donde cada parámetro de `S` es en sí mismo un tipo muestreable; devuelve un valor del tipo `S`. Tenga en cuenta que tipos de tupla como `Tuple{Vararg{T}}` (tamaño desconocido) y `Tuple{1:2}` (parametrizado con un valor) no son compatibles
      * un tipo `Pair`, por ejemplo `Pair{X, Y}` tal que `rand` está definido para `X` y `Y`, en cuyo caso se producen pares aleatorios.

`S` por defecto es [`Float64`](@ref). Cuando solo se pasa un argumento además del opcional `rng` y es un `Tuple`, se interpreta como una colección de valores (`S`) y no como `dims`.

Vea también [`randn`](@ref) para números distribuidos normalmente, y [`rand!`](@ref) y [`randn!`](@ref) para los equivalentes en su lugar.

!!! compat "Julia 1.1"
    El soporte para `S` como una tupla requiere al menos Julia 1.1.


!!! compat "Julia 1.11"
    El soporte para `S` como un tipo `Tuple` requiere al menos Julia 1.11.


# Ejemplos

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> using Random

julia> rand(Xoshiro(0), Dict(1=>2, 3=>4))
3 => 4

julia> rand((2, 3))
3

julia> rand(Float64, (2, 3))
2×3 Array{Float64,2}:
 0.999717  0.0143835  0.540787
 0.696556  0.783855   0.938235
```

!!! note
    La complejidad de `rand(rng, s::Union{AbstractDict,AbstractSet})` es lineal en la longitud de `s`, a menos que un método optimizado con complejidad constante esté disponible, que es el caso para `Dict`, `Set` y `BitSet`s densos. Para más de unas pocas llamadas, use `rand(rng, collect(s))` en su lugar, o bien `rand(rng, Dict(s))` o `rand(rng, Set(s))` según corresponda.

