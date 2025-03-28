```
joinpath(parts::AbstractString...) -> String
joinpath(parts::Vector{AbstractString}) -> String
joinpath(parts::Tuple{AbstractString}) -> String
```

Une los componentes de la ruta en una ruta completa. Si algún argumento es una ruta absoluta o (en Windows) tiene una especificación de unidad que no coincide con la unidad calculada para la unión de las rutas anteriores, entonces se descartan los componentes anteriores.

Nota sobre Windows: dado que hay un directorio actual para cada unidad, `joinpath("c:", "foo")` representa una ruta relativa al directorio actual en la unidad "c:", por lo que esto es igual a "c:foo", no "c:\foo". Además, `joinpath` trata esto como una ruta no absoluta e ignora la capitalización de la letra de la unidad, por lo tanto, `joinpath("C:\A","c:b") = "C:\A\b"`.

# Ejemplos

```jldoctest
julia> joinpath("/home/myuser", "example.jl")
"/home/myuser/example.jl"
```

```jldoctest
julia> joinpath(["/home/myuser", "example.jl"])
"/home/myuser/example.jl"
```
