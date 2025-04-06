```
UndefRefError()
```

Verilen nesne için öğe veya alan tanımlı değil.

# Örnekler

```jldoctest
julia> struct MyType
           a::Vector{Int}
           MyType() = new()
       end

julia> A = MyType()
MyType(#undef)

julia> A.a
HATA: UndefRefError: tanımsız referansa erişim
Yığın izi:
[...]
```
