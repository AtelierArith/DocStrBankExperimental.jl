```
randstring([rng=default_rng()], [chars], [len=8])
```

Crea una cadena aleatoria de longitud `len`, que consiste en caracteres de `chars`, que por defecto es el conjunto de letras mayúsculas y minúsculas y los dígitos 0-9. El argumento opcional `rng` especifica un generador de números aleatorios, consulta [Random Numbers](@ref).

# Ejemplos

```jldoctest
julia> Random.seed!(3); randstring()
"Lxz5hUwn"

julia> randstring(Xoshiro(3), 'a':'z', 6)
"iyzcsm"

julia> randstring("ACGT")
"TGCTCCTC"
```

!!! nota
    `chars` puede ser cualquier colección de caracteres, de tipo `Char` o `UInt8` (más eficiente), siempre que [`rand`](@ref) pueda seleccionar caracteres aleatoriamente de ella.

