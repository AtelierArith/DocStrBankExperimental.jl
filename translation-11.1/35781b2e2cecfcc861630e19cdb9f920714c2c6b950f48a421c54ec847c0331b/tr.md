```
only(x)
```

Koleksiyon `x`'in tek ve yegâne elemanını döndürür veya koleksiyonun sıfır veya birden fazla elemanı varsa [`ArgumentError`](@ref) fırlatır.

Ayrıca bkz. [`first`](@ref), [`last`](@ref).

!!! compat "Julia 1.4"
    Bu yöntem en az Julia 1.4 gerektirir.


# Örnekler

```jldoctest
julia> only(["a"])
"a"

julia> only("a")
'a': ASCII/Unicode U+0061 (kategori Ll: Küçük harf, harf)

julia> only(())
HATA: ArgumentError: Tuple 0 eleman içeriyor, tam olarak 1 eleman içermelidir
Yığın izi:
[...]

julia> only(('a', 'b'))
HATA: ArgumentError: Tuple 2 eleman içeriyor, tam olarak 1 eleman içermelidir
Yığın izi:
[...]
```
