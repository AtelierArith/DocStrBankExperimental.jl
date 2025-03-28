```
bytesavailable(io)
```

Gibt die Anzahl der Bytes zurück, die zum Lesen verfügbar sind, bevor ein Lesevorgang aus diesem Stream oder Puffer blockiert.

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation");

julia> bytesavailable(io)
34
```
