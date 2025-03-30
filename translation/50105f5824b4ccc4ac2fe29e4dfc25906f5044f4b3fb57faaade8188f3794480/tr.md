```
Dict([itr])
```

`Dict{K,V}()` bir `K` türünde anahtarlar ve `V` türünde değerler içeren bir hash tablosu oluşturur. Anahtarlar [`isequal`](@ref) ile karşılaştırılır ve [`hash`](@ref) ile hashlenir.

Tek bir iterable argüman verildiğinde, argümandan üretilen 2-tuple `(anahtar,değer)` çiftlerinden oluşan bir [`Dict`](@ref) oluşturur.

# Örnekler

```jldoctest
julia> Dict([("A", 1), ("B", 2)])
Dict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```

Alternatif olarak, bir dizi çift argüman da geçirilebilir.

```jldoctest
julia> Dict("A"=>1, "B"=>2)
Dict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```

!!! uyarı     Anahtarların değiştirilebilir olmasına izin verilir, ancak eğer saklanan anahtarları değiştirirseniz, hash tablosu içsel olarak tutarsız hale gelebilir; bu durumda `Dict` düzgün çalışmayacaktır. Anahtarları değiştirmek zorundaysanız [`IdDict`](@ref) alternatif olabilir.
