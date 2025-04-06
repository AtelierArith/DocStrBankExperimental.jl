```
findlast(ch::AbstractChar, string::AbstractString)
```

Karakter `ch`'nin `string` içindeki son geçişini bulur.

!!! uyum "Julia 1.3"
    Bu yöntem en az Julia 1.3 gerektirir.


# Örnekler

```jldoctest
julia> findlast('p', "happy")
4

julia> findlast('z', "happy") === nothing
true
```
