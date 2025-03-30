```
mmap(io::Union{IOStream,AbstractString,Mmap.AnonymousMmap}[, type::Type{Array{T,N}}, dims, offset]; grow::Bool=true, shared::Bool=true)
mmap(type::Type{Array{T,N}}, dims)
```

Bir dosyaya bağlı değerleri olan bir `Array` oluşturun, bellek eşlemesi kullanarak. Bu, bilgisayarın belleğine sığmayacak kadar büyük verilerle çalışmanın pratik bir yolunu sağlar.

Tür, `T`'nin bit türü elemanına ve dizinin `N`'ye sahip bir `Array{T,N}`'dir; bu, dizinin baytlarının nasıl yorumlanacağını belirler. Dosyanın ikili formatta saklanması gerektiğini ve format dönüşümlerinin mümkün olmadığını unutmayın (bu, işletim sistemlerinin bir sınırlamasıdır, Julia'nın değil).

`dims`, dizinin boyutunu veya uzunluğunu belirten bir demet veya tek bir [`Integer`](@ref) olarak belirtilir.

Dosya, ya açık bir [`IOStream`](@ref) ya da dosya adı dizesi olarak akış argümanı aracılığıyla geçilir. Akışı başlatırken, "salt okunur" bir dizi için `"r"` ve diske değer yazmak için yeni bir dizi oluşturmak için `"w+"` kullanın.

Eğer `type` argümanı belirtilmemişse, varsayılan `Vector{UInt8}`'dir.

Örneğin, dosyadaki bir başlığı atlamak istiyorsanız, isteğe bağlı olarak bir offset (bayt cinsinden) belirtebilirsiniz. Offset için varsayılan değer, bir `IOStream` için mevcut akış konumudur.

`grow` anahtar kelime argümanı, istenen dizi boyutunu karşılamak için disk dosyasının büyütülüp büyütülmeyeceğini belirtir (eğer toplam dosya boyutu < istenen dizi boyutu). Dosyayı büyütmek için yazma ayrıcalıkları gereklidir.

`shared` anahtar kelime argümanı, elde edilen `Array` ve ona yapılan değişikliklerin, aynı dosyayı eşleyen diğer süreçler tarafından görünür olup olmayacağını belirtir.

Örneğin, aşağıdaki kod

```julia
# mmapping için bir dosya oluştur
# (bu adımı yapmak için mmap kullanabilirsiniz)
using Mmap
A = rand(1:20, 5, 30)
s = open("/tmp/mmap.bin", "w+")
# Dizinin boyutlarını dosyadaki ilk iki Int olarak yazacağız
write(s, size(A,1))
write(s, size(A,2))
# Şimdi verileri yaz
write(s, A)
close(s)

# Geri okuyarak test et
s = open("/tmp/mmap.bin")   # varsayılan salt okunur
m = read(s, Int)
n = read(s, Int)
A2 = mmap(s, Matrix{Int}, (m,n))
```

`m`-çarpı-`n` `Matrix{Int}` oluşturur ve bu, `s` akışıyla ilişkili dosyaya bağlıdır.

Daha taşınabilir bir dosya, kelime boyutunu – 32 bit veya 64 bit – ve sonlandırma bilgilerini başlıkta kodlamalıdır. Pratikte, ikili verileri HDF5 gibi standart formatlar kullanarak kodlamayı düşünün (bu, bellek eşlemesi ile kullanılabilir).
