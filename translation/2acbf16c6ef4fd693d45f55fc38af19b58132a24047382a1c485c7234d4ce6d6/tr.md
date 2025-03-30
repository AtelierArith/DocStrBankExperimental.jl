```
bytes2hex(itr) -> String
bytes2hex(io::IO, itr)
```

Bir `itr` baytları iteratörünü onaltılık dize temsilini dönüştürür; ya `bytes2hex(itr)` ile bir `String` döndürür ya da `bytes2hex(io, itr)` ile dizeyi bir `io` akışına yazar. Onaltılık karakterler tamamen küçük harflerdir.

!!! compat "Julia 1.7"
    `UInt8` değerleri üreten rastgele iteratörlerle `bytes2hex` çağırmak, Julia 1.7 veya daha yenisini gerektirir. Daha eski sürümlerde, `bytes2hex` çağırmadan önce iteratörü `collect` edebilirsiniz.


# Örnekler

```jldoctest
julia> a = string(12345, base = 16)
"3039"

julia> b = hex2bytes(a)
2-element Vector{UInt8}:
 0x30
 0x39

julia> bytes2hex(b)
"3039"
```
