```
normpath(path::AbstractString) -> String
```

Bir yolu normalize eder, "." ve ".." girişlerini kaldırır ve "/" karakterini sistem için kanonik yol ayırıcıya değiştirir.

# Örnekler

```jldoctest
julia> normpath("/home/myuser/../example.jl")
"/home/example.jl"

julia> normpath("Documents/Julia") == joinpath("Documents", "Julia")
true
```
