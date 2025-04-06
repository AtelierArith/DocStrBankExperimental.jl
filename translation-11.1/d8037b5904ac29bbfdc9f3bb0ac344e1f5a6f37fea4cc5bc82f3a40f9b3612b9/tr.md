```
LibGit2.DiffDelta
```

Bir girişteki değişikliklerin tanımı. [`git_diff_delta`](https://libgit2.org/libgit2/#HEAD/type/git_diff_delta) yapısıyla eşleşir.

Alanlar şunları temsil eder:

  * `status`: Dosyanın eklenip/ değiştirilip/ silinmediğini belirten `Consts.DELTA_STATUS`'dan biri.
  * `flags`: Delta ve her iki taraftaki nesneler için bayraklar. Dosyaların ikisini de ikili/metin olarak ele alınıp alınmayacağını, her iki tarafta da mevcut olup olmadıklarını ve nesne kimliklerinin doğru olduğunun bilinip bilinmediğini belirler.
  * `similarity`: Bir dosyanın yeniden adlandırılıp adlandırılmadığını veya kopyalanıp kopyalanmadığını belirtmek için kullanılır.
  * `nfiles`: Delta içindeki dosya sayısı (örneğin, delta bir alt modül taahhüt kimliği üzerinde çalıştırıldıysa, birden fazla dosya içerebilir).
  * `old_file`: Değişikliklerden önceki dosya(lar) hakkında bilgi içeren bir [`DiffFile`](@ref).
  * `new_file`: Değişikliklerden sonraki dosya(lar) hakkında bilgi içeren bir [`DiffFile`](@ref).
