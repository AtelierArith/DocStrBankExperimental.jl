```
hex2bytes(itr)
```

Bir dizi onaltılık basamak için ASCII kodlarının `itr` adlı bir yineleyicisi verildiğinde, dönen `Vector{UInt8}` türünde baytların ikili temsilini döndürür: `itr` içindeki her ardışık onaltılık basamak çifti, dönen vektörde bir baytın değerini verir.

`itr`'nin uzunluğu çift olmalıdır ve dönen dizi `itr`'nin uzunluğunun yarısı kadar olacaktır. Ayrıca [`hex2bytes!`](@ref) yerinde bir sürüm için ve [`bytes2hex`](@ref) tersine dönüşüm için bakınız.

!!! compat "Julia 1.7"
    `UInt8` değerleri üreten yineleyicilerle `hex2bytes` çağrısı yapmak, Julia 1.7 veya daha yenisini gerektirir. Daha eski sürümlerde, `hex2bytes`'ı çağırmadan önce yineleyiciyi `collect` edebilirsiniz.


# Örnekler

```jldoctest
julia> s = string(12345, base = 16)
"3039"

julia> hex2bytes(s)
2-element Vector{UInt8}:
 0x30
 0x39

julia> a = b"01abEF"
6-element Base.CodeUnits{UInt8, String}:
 0x30
 0x31
 0x61
 0x62
 0x45
 0x46

julia> hex2bytes(a)
3-element Vector{UInt8}:
 0x01
 0xab
 0xef
```
