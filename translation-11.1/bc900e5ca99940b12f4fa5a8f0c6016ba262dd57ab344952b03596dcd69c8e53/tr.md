```
IteratorEltype(itertype::Type) -> IteratorEltype
```

Bir iteratörün türü verildiğinde, aşağıdaki değerlerden birini döndür:

  * `EltypeUnknown()` eğer iteratör tarafından üretilen elemanların türü önceden bilinmiyorsa.
  * `HasEltype()` eğer eleman türü biliniyorsa ve [`eltype`](@ref) anlamlı bir değer döndürecekse.

`HasEltype()` varsayılan değerdir, çünkü iteratörlerin [`eltype`](@ref) uyguladığı varsayılmaktadır.

Bu özellik genellikle belirli bir sonuç türü önceden tahsis eden algoritmalar ile üretilen değerlerin türlerine dayalı olarak bir sonuç türü seçen algoritmalar arasında seçim yapmak için kullanılır.

```jldoctest
julia> Base.IteratorEltype(1:5)
Base.HasEltype()
```
