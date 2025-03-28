```
joinpath(parts::AbstractString...) -> String
joinpath(parts::Vector{AbstractString}) -> String
joinpath(parts::Tuple{AbstractString}) -> String
```

Joindre des composants de chemin en un chemin complet. Si un argument est un chemin absolu ou (sur Windows) a une spécification de lecteur qui ne correspond pas au lecteur calculé pour la jonction des chemins précédents, alors les composants précédents sont supprimés.

Note sur Windows, puisque chaque lecteur a un répertoire courant, `joinpath("c:", "foo")` représente un chemin relatif au répertoire courant sur le lecteur "c:", donc cela est égal à "c:foo", pas "c:\foo". De plus, `joinpath` traite cela comme un chemin non absolu et ignore la casse de la lettre du lecteur, donc `joinpath("C:\A","c:b") = "C:\A\b"`.

# Exemples

```jldoctest
julia> joinpath("/home/myuser", "example.jl")
"/home/myuser/example.jl"
```

```jldoctest
julia> joinpath(["/home/myuser", "example.jl"])
"/home/myuser/example.jl"
```
