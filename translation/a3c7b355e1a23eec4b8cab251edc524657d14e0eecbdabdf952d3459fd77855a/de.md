```
joinpath(parts::AbstractString...) -> String
joinpath(parts::Vector{AbstractString}) -> String
joinpath(parts::Tuple{AbstractString}) -> String
```

Fügt Pfadkomponenten zu einem vollständigen Pfad zusammen. Wenn ein Argument ein absoluter Pfad ist oder (unter Windows) eine Laufwerkspezifikation hat, die nicht mit dem für die Verbindung der vorhergehenden Pfade berechneten Laufwerk übereinstimmt, werden vorherige Komponenten verworfen.

Hinweis zu Windows: Da es für jedes Laufwerk ein aktuelles Verzeichnis gibt, stellt `joinpath("c:", "foo")` einen Pfad dar, der relativ zum aktuellen Verzeichnis auf Laufwerk "c:" ist, sodass dies gleichbedeutend mit "c:foo" ist, nicht mit "c:\foo". Darüber hinaus behandelt `joinpath` dies als einen nicht absoluten Pfad und ignoriert die Groß- und Kleinschreibung des Laufwerksbuchstabens, daher gilt `joinpath("C:\A","c:b") = "C:\A\b"`.

# Beispiele

```jldoctest
julia> joinpath("/home/myuser", "example.jl")
"/home/myuser/example.jl"
```

```jldoctest
julia> joinpath(["/home/myuser", "example.jl"])
"/home/myuser/example.jl"
```
