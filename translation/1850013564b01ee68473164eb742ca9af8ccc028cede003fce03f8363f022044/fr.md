```
Unicode.julia_chartransform(c::Union{Char,Integer})
```

Mappez le caractère Unicode (`Char`) ou le point de code (`Integer`) `c` au caractère ou point de code "équivalent" correspondant, respectivement, selon l'équivalence personnalisée utilisée dans le parseur Julia (en plus de la normalisation NFC).

Par exemple, `'µ'` (U+00B5 micro) est traité comme équivalent à `'μ'` (U+03BC mu) par le parseur de Julia, donc `julia_chartransform` effectue cette transformation tout en laissant les autres caractères inchangés :

```jldoctest
julia> Unicode.julia_chartransform('µ')
'μ': Unicode U+03BC (catégorie Ll: Lettre, minuscule)

julia> Unicode.julia_chartransform('x')
'x': ASCII/Unicode U+0078 (catégorie Ll: Lettre, minuscule)
```

`julia_chartransform` est principalement utile pour être passé à la fonction [`Unicode.normalize`](@ref) afin d'imiter la normalisation utilisée par le parseur Julia :

```jldoctest
julia> s = "µö"
"µö"

julia> s2 = Unicode.normalize(s, compose=true, stable=true, chartransform=Unicode.julia_chartransform)
"μö"

julia> collect(s2)
2-element Vector{Char}:
 'μ': Unicode U+03BC (catégorie Ll: Lettre, minuscule)
 'ö': Unicode U+00F6 (catégorie Ll: Lettre, minuscule)

julia> s2 == string(Meta.parse(s))
true
```

!!! compat "Julia 1.8"
    Cette fonction a été introduite dans Julia 1.8.

