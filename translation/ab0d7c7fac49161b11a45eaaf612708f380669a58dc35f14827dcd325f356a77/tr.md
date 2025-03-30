```
summary(io::IO, x)
str = summary(x)
```

Bir akışa `io` yazdırır veya bir değer hakkında kısa bir açıklama veren bir dize `str` döndürür. Varsayılan olarak `string(typeof(x))` döner, örneğin [`Int64`](@ref).

Diziler için, boyut ve tür bilgilerini içeren bir dize döner, örneğin `10-element Array{Int64,1}`.

# Örnekler

```jldoctest
julia> summary(1)
"Int64"

julia> summary(zeros(2))
"2-element Vector{Float64}"
```
