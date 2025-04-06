```
DivideError()
```

Tam bölmesi 0 olan bir payda değeri ile denendi.

# Örnekler

```jldoctest
julia> 2/0
Inf

julia> div(2, 0)
HATA: DivideError: tam bölme hatası
Yığın izi:
[...]
```
