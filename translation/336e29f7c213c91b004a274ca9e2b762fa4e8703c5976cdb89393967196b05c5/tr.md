```
sizeof(str::AbstractString)
```

`str`'nin bayt cinsinden boyutu. `str`'deki kod birimlerinin sayısı ile `str`'deki bir kod biriminin bayt cinsinden boyutunun çarpımına eşittir.

# Örnekler

```jldoctest
julia> sizeof("")
0

julia> sizeof("∀")
3
```
