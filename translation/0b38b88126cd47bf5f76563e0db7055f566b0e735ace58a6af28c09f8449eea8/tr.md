```
AbstractWorkerPool
```

[`WorkerPool`](@ref) ve [`CachingPool`](@ref) gibi işçi havuzları için süper tip. Bir `AbstractWorkerPool` şunları uygulamalıdır:

  * [`push!`](@ref) - genel havuza (mevcut + meşgul) yeni bir işçi ekle
  * [`put!`](@ref) - bir işçiyi mevcut havuza geri koy
  * [`take!`](@ref) - mevcut havuzdan bir işçi al (uzaktan fonksiyon yürütmek için kullanılacak)
  * [`length`](@ref) - genel havuzda mevcut olan işçi sayısı
  * [`isready`](@ref) - havuzda bir `take!` işleminin engelleneceği durumda false, aksi takdirde true döndür

Yukarıdakilerin varsayılan uygulamaları (bir `AbstractWorkerPool` üzerinde) aşağıdaki alanları gerektirir:

  * `channel::Channel{Int}`
  * `workers::Set{Int}`

burada `channel` serbest işçi pid'lerini ve `workers` bu havuzla ilişkili tüm işçilerin kümesini içerir.
