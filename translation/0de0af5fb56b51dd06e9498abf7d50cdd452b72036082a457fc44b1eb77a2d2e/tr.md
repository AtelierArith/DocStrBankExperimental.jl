```
codeunit(s::AbstractString, i::Integer) -> Union{UInt8, UInt16, UInt32}
```

Dize `s` içindeki `i` indeksindeki kod birimi değerini döndürür. Şunu unutmayın

```
codeunit(s, i) :: codeunit(s)
```

Yani, `codeunit(s, i)` tarafından döndürülen değer, `codeunit(s)` tarafından döndürülen türdedir.

# Örnekler

```jldoctest
julia> a = codeunit("Hello", 2)
0x65

julia> typeof(a)
UInt8
```

Ayrıca bkz. [`ncodeunits`](@ref), [`checkbounds`](@ref).
