```
Slices{P,SM,AX,S,N} <: AbstractSlices{S,N}
```

Belirli boyut(lar) üzerinden bir üst diziye dilimler içeren bir `AbstractArray`, diğer boyut(lar)dan tüm verileri seçen görünümler döndürür.

Bunlar genellikle [`eachslice`](@ref), [`eachcol`](@ref) veya [`eachrow`](@ref) ile oluşturulmalıdır.

[`parent(s::Slices)`](@ref) üst diziyi döndürecektir.
