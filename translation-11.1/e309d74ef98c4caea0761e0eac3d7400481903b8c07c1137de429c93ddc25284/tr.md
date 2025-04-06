```
take!(b::IOBuffer)
```

Bir `IOBuffer`'ın içeriğini bir dizi olarak alın. Sonrasında, `IOBuffer` başlangıç durumuna sıfırlanır.

# Örnekler

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."
```
