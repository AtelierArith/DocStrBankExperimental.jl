```
open(f::Function, args...; kwargs...)
```

`open(args...; kwargs...)` sonucunu `f` fonksiyonuna uygular ve tamamlandığında elde edilen dosya tanımlayıcısını kapatır.

# Örnekler

```jldoctest
julia> write("myfile.txt", "Hello world!");

julia> open(io->read(io, String), "myfile.txt")
"Hello world!"

julia> rm("myfile.txt")
```
