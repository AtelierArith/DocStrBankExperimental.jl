```
sizeof(str::AbstractString)
```

Größe in Bytes des Strings `str`. Entspricht der Anzahl der Codeeinheiten in `str` multipliziert mit der Größe in Bytes einer Codeeinheit in `str`.

# Beispiele

```jldoctest
julia> sizeof("")
0

julia> sizeof("∀")
3
```
