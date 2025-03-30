```
IteratorSize(itertype::Type) -> IteratorSize
```

Bir iteratörün türü verildiğinde, aşağıdaki değerlerden birini döndür:

  * `SizeUnknown()` eğer uzunluk (öğe sayısı) önceden belirlenemiyorsa.
  * `HasLength()` eğer sabit, sonlu bir uzunluk varsa.
  * `HasShape{N}()` eğer bilinen bir uzunluk artı çok boyutlu şekil kavramı varsa (bir dizi gibi). Bu durumda `N`, boyut sayısını vermeli ve [`axes`](@ref) fonksiyonu iteratör için geçerlidir.
  * `IsInfinite()` eğer iteratör sonsuza kadar değerler üretiyorsa.

Varsayılan değer (bu fonksiyonu tanımlamayan iteratörler için) `HasLength()`'dır. Bu, çoğu iteratörün [`length`](@ref) uyguladığını varsaydığı anlamına gelir.

Bu özellik genellikle sonuçları için alanı önceden ayıran algoritmalar ile sonuçlarını kademeli olarak yeniden boyutlandıran algoritmalar arasında seçim yapmak için kullanılır.

```jldoctest
julia> Base.IteratorSize(1:5)
Base.HasShape{1}()

julia> Base.IteratorSize((2,3))
Base.HasLength()
```
