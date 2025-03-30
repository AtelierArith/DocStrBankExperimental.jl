```
read(s::IO, nb=typemax(Int))
```

`s`'den en fazla `nb` bayt okuyun ve okunan baytların `Vector{UInt8}`'sini döndürün.
