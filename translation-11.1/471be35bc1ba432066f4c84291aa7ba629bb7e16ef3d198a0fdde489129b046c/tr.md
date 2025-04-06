```
InexactError(name::Symbol, T, val)
```

`val`'ı `T` türüne tam olarak dönüştüremiyor `name` fonksiyonunun bir yönteminde.

# Örnekler

```jldoctest
julia> convert(Float64, 1+2im)
HATA: InexactError: Float64(1 + 2im)
Yığın İzleme:
[...]
```
