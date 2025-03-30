```
reinterpret(T::DataType, A::AbstractArray)
```

Verilen dizinin aynı ikili verilerine sahip bir görünümünü oluşturur, ancak `T` eleman türü olarak kullanılır.

Bu işlev, elemanları açıkça alınana kadar hesaplanmayan "tembel" diziler üzerinde de çalışır. Örneğin, `reinterpret` aralığı `1:6` üzerinde, yoğun vektör `collect(1:6)` üzerinde olduğu gibi çalışır:

```jldoctest
julia> reinterpret(Float32, UInt32[1 2 3 4 5])
1×5 reinterpret(Float32, ::Matrix{UInt32}):
 1.0f-45  3.0f-45  4.0f-45  6.0f-45  7.0f-45

julia> reinterpret(Complex{Int}, 1:6)
3-element reinterpret(Complex{Int64}, ::UnitRange{Int64}):
 1 + 2im
 3 + 4im
 5 + 6im
```

Eğer `T` ile `eltype(A)` arasındaki dolgu bitlerinin konumu hizalanmazsa, sonuçta oluşan dizi yalnızca okunabilir veya yalnızca yazılabilir olacaktır; bu, geçersiz bitlerin yazılmasını veya okunmasını önlemek içindir.

```jldoctest
julia> a = reinterpret(Tuple{UInt8, UInt32}, UInt32[1, 2])
1-element reinterpret(Tuple{UInt8, UInt32}, ::Vector{UInt32}):
 (0x01, 0x00000002)

julia> a[1] = 3
HATA: Tuple{UInt8, UInt32} türünün dolgusu UInt32 türü ile uyumlu değildir.

julia> b = reinterpret(UInt32, Tuple{UInt8, UInt32}[(0x01, 0x00000002)]); # gösterim hatası verecektir

julia> b[1]
HATA: UInt32 türünün dolgusu Tuple{UInt8, UInt32} türü ile uyumlu değildir.
```
