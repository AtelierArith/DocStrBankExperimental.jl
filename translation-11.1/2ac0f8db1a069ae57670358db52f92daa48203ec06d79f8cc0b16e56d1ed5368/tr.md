```
SharedArray{T}(dims::NTuple; init=false, pids=Int[])
SharedArray{T,N}(...)
```

Bir `SharedArray` oluşturur, bit türü `T` ve boyut `dims` ile belirtilen `pids` süreçleri arasında - bunların hepsi aynı ana makinede olmalıdır. `N`, `SharedArray{T,N}(dims)` çağrılarak belirtilirse, `N` boyutların uzunluğuyla eşleşmelidir.

`pids` belirtilmezse, paylaşılan dizi mevcut ana makinedeki tüm süreçler arasında, ana süreç dahil olmak üzere haritalanır. Ancak, `localindices` ve `indexpids` yalnızca işçi süreçlerine atıfta bulunacaktır. Bu, iş dağıtım kodunun, ana sürecin bir sürücü olarak hareket ettiği durumlarda, gerçek hesaplama için işçileri kullanmasını kolaylaştırır.

`init` türünde bir `initfn(S::SharedArray)` fonksiyonu belirtilirse, bu, katılan tüm işçi süreçlerinde çağrılır.

Paylaşılan dizi, haritalamanın oluşturulduğu düğümde `SharedArray` nesnesine bir referans var olduğu sürece geçerlidir.

```
SharedArray{T}(filename::AbstractString, dims::NTuple, [offset=0]; mode=nothing, init=false, pids=Int[])
SharedArray{T,N}(...)
```

`filename` dosyası ile desteklenen bir `SharedArray` oluşturur, eleman türü `T` (bir bit türü olmalıdır) ve boyut `dims`, belirtilen `pids` süreçleri arasında - bunların hepsi aynı ana makinede olmalıdır. Bu dosya ana makine belleğine mmapped edilir, aşağıdaki sonuçlarla birlikte:

  * Dizi verileri ikili formatta temsil edilmelidir (örneğin, CSV gibi bir ASCII formatı desteklenemez)
  * Dizi değerlerinde yaptığınız herhangi bir değişiklik (örneğin, `A[3] = 0`) disk üzerindeki değerleri de değiştirecektir

`pids` belirtilmezse, paylaşılan dizi mevcut ana makinedeki tüm süreçler arasında, ana süreç dahil olmak üzere haritalanır. Ancak, `localindices` ve `indexpids` yalnızca işçi süreçlerine atıfta bulunacaktır. Bu, iş dağıtım kodunun, ana sürecin bir sürücü olarak hareket ettiği durumlarda, gerçek hesaplama için işçileri kullanmasını kolaylaştırır.

`mode`, `"r"`, `"r+"`, `"w+"` veya `"a+"`'dan biri olmalıdır ve `filename` ile belirtilen dosya zaten mevcutsa varsayılan olarak `"r+"`, değilse `"w+"` olarak ayarlanır. `init` türünde bir `initfn(S::SharedArray)` fonksiyonu belirtilirse, bu, katılan tüm işçi süreçlerinde çağrılır. Dosya yazılabilir değilse bir `init` fonksiyonu belirleyemezsiniz.

`offset`, dosyanın başındaki belirtilen byte sayısını atlamanıza olanak tanır.
