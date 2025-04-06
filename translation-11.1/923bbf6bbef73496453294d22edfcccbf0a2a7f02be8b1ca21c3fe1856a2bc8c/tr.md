```
splitext(path::AbstractString) -> (String, String)
```

Eğer bir yolun son bileşeni bir veya daha fazla nokta içeriyorsa, yolu son noktadan önceki her şey ve nokta dahil ve sonrasındaki her şey olarak ayırın. Aksi takdirde, argümanı değiştirilmemiş olarak ve boş bir dize ile bir demet döndürün. "splitext" uzantıyı ayırmak için kısaltmadır.

# Örnekler

```jldoctest
julia> splitext("/home/myuser/example.jl")
("/home/myuser/example", ".jl")

julia> splitext("/home/myuser/example.tar.gz")
("/home/myuser/example.tar", ".gz")

julia> splitext("/home/my.user/example")
("/home/my.user/example", "")
```
