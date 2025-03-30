```
@time_imports
```

Bir ifadeyi yürütmek ve paketlerin ve bunların bağımlılıklarının içeriği için harcanan zamanı raporlamak üzere bir makro. Herhangi bir derleme süresi bir yüzde olarak rapor edilecek ve eğer varsa hangi kısmının yeniden derleme olduğu belirtilecektir.

Her paket veya paket uzantısı için bir satır yazdırılır. Gösterilen süre, o paketin kendisini içe aktarmak için harcanan zamandır, bağımlılıklarının yüklenmesi için harcanan zamanı içermez.

Julia 1.9+ [paket uzantıları](@ref man-extensions) Ana → Uzantı olarak gösterilecektir.

!!! not
    Yükleme süreci sırasında bir paket, yalnızca doğrudan bağımlılıklarını değil, tüm bağımlılıklarını sıralı bir şekilde içe aktarır.


```julia-repl
julia> @time_imports using CSV
     50.7 ms  Parsers 17.52% derleme süresi
      0.2 ms  DataValueInterfaces
      1.6 ms  DataAPI
      0.1 ms  IteratorInterfaceExtensions
      0.1 ms  TableTraits
     17.5 ms  Tables
     26.8 ms  PooledArrays
    193.7 ms  SentinelArrays 75.12% derleme süresi
      8.6 ms  InlineStrings
     20.3 ms  WeakRefStrings
      2.0 ms  TranscodingStreams
      1.4 ms  Zlib_jll
      1.8 ms  CodecZlib
      0.8 ms  Compat
     13.1 ms  FilePathsBase 28.39% derleme süresi
   1681.2 ms  CSV 92.40% derleme süresi
```

!!! uyumluluk "Julia 1.8"
    Bu makro en az Julia 1.8 gerektirir.

