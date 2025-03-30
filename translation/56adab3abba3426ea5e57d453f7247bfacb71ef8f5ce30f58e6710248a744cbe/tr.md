```
findnext(ch::AbstractChar, string::AbstractString, start::Integer)
```

`ch` karakterinin `start` konumundan başlayarak `string` içinde bir sonraki geçişini bulur.

!!! compat "Julia 1.3"
    Bu yöntem en az Julia 1.3 gerektirir.


# Örnekler

```jldoctest
julia> findnext('z', "Hello to the world", 1) === nothing
true

julia> findnext('o', "Hello to the world", 6)
8
```
