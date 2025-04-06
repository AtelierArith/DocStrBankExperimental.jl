```
Pair(x, y)
x => y
```

Construya un objeto `Pair` con el tipo `Pair{typeof(x), typeof(y)}`. Los elementos se almacenan en los campos `first` y `second`. También se pueden acceder a través de la iteración (pero un `Pair` se trata como un único "escalar" para las operaciones de difusión).

Véase también [`Dict`](@ref).

# Ejemplos

```jldoctest
julia> p = "foo" => 7
"foo" => 7

julia> typeof(p)
Pair{String, Int64}

julia> p.first
"foo"

julia> for x in p
           println(x)
       end
foo
7

julia> replace.(["xops", "oxps"], "x" => "o")
2-element Vector{String}:
 "oops"
 "oops"
```
