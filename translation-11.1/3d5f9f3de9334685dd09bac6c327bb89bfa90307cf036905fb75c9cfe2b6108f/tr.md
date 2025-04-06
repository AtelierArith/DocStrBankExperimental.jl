```
BitArray{N} <: AbstractArray{Bool, N}
```

Alanı sadece bir bit kullanarak boolean değerler için `N`-boyutlu alanı verimli bir şekilde depolayan `BitArray`.

`BitArray`'ler her 8 baytta 64 değere kadar paketlenir, bu da `Array{Bool, N}` üzerinde 8 kat alan verimliliği sağlar ve bazı işlemlerin aynı anda 64 değer üzerinde çalışmasına olanak tanır.

Varsayılan olarak, Julia, boolean elemanlar üreten [yayılma](@ref Broadcasting) işlemlerinden (dotted-comparisons gibi `.==` dahil) ve [`trues`](@ref) ile [`falses`](@ref) fonksiyonlarından `BitArrays` döndürür.

!!! not
    Paketlenmiş depolama formatı nedeniyle, en az birinin yazma olduğu `BitArray` elemanlarına eşzamanlı erişim, iş parçacığı güvenli değildir.

