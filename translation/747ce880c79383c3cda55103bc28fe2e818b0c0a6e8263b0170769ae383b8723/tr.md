```
chomp(s::AbstractString) -> SubString
```

Bir dize üzerindeki tek bir son satır sonunu kaldırır.

Ayrıca bkz. [`chop`](@ref).

# Örnekler

```jldoctest
julia> chomp("Hello\n")
"Hello"
```
