```
bytesavailable(io)
```

Bu akış veya tampondan bir okuma engellenmeden önce okunabilir durumda olan bayt sayısını döndürür.

# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> bytesavailable(io)
34
```
