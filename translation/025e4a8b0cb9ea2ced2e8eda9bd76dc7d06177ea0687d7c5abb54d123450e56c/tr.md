```
length(s::AbstractString) -> Int
length(s::AbstractString, i::Integer, j::Integer) -> Int
```

Dize `s` dizisindeki `i` ile `j` indeksleri arasındaki karakter sayısını döndürür.

Bu, `i` ile `j` arasındaki geçerli karakter indeksleri olan kod birimi indekslerinin sayısı olarak hesaplanır. Sadece tek bir dize argümanı ile, bu tüm dizideki karakter sayısını hesaplar. `i` ve `j` argümanları ile, `s` dizisinde geçerli indeksler olan `i` ile `j` arasındaki (dahil) indekslerin sayısını hesaplar. Sınır içindeki değerlere ek olarak, `i` sınır dışı değeri `ncodeunits(s) + 1` alabilir ve `j` sınır dışı değeri `0` alabilir.

!!! note
    Bu işlemin zaman karmaşıklığı genel olarak lineerdir. Yani, dizedeki bayt veya karakter sayısına orantılı bir zaman alacaktır çünkü değeri anlık olarak sayar. Bu, diziler için olan yöntemle karşılaştırıldığında, sabit zamanlı bir işlemdir.


Ayrıca bkz. [`isvalid`](@ref), [`ncodeunits`](@ref), [`lastindex`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref).

# Örnekler

```jldoctest
julia> length("jμΛIα")
5
```
