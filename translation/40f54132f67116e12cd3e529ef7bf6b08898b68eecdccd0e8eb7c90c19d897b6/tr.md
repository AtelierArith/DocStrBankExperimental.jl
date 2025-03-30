```
print([io::IO = stdout,] [data::Vector = fetch()], [lidict::Union{LineInfoDict, LineInfoFlatDict} = getdict(data)]; kwargs...)
```

Profiling sonuçlarını `io`ya (varsayılan olarak `stdout`) yazdırır. Eğer bir `data` vektörü sağlamazsanız, birikmiş geri izlerin içsel tamponu kullanılacaktır.

Anahtar argümanlar herhangi bir kombinasyon olabilir:

  * `format` – Geri izlerin ağaç yapısını gösteren (varsayılan, `:tree`) veya göstermeyen (`:flat`) girintili olarak yazdırılıp yazdırılmayacağını belirler.
  * `C` – Eğer `true` ise, C ve Fortran kodlarından geri izler gösterilir (normalde hariç tutulur).
  * `combine` – Eğer `true` (varsayılan), aynı kod satırına karşılık gelen talimat işaretçileri birleştirilir.
  * `maxdepth` – `:tree` formatında `maxdepth`'ten daha derinliği sınırlar.
  * `sortedby` – `:flat` formatındaki sıralamayı kontrol eder. `:filefuncline` (varsayılan) kaynak satırına göre sıralar, `:count` toplanan örnek sayısına göre sıralar ve `:overhead` her fonksiyonun kendisi tarafından neden olunan örnek sayısına göre sıralar.
  * `groupby` – Görevler ve iş parçacıkları üzerinde gruplamayı veya gruplama olmamasını kontrol eder. Seçenekler `:none` (varsayılan), `:thread`, `:task`, `[:thread, :task]` veya `[:task, :thread]`'dir; son iki seçenek iç içe gruplama sağlar.
  * `noisefloor` – Örneklerin sezgisel gürültü tabanını aşan çerçeveleri sınırlar (sadece `:tree` formatına uygulanır). Bunun için denemek için önerilen bir değer 2.0'dır (varsayılan 0'dır). Bu parametre, `n <= noisefloor * √N` olan satırlar için örnekleri gizler; burada `n` bu satırdaki örnek sayısı ve `N` çağrılan için örnek sayısıdır.
  * `mincount` – Yazdırmayı yalnızca en az `mincount` kez bulunan satırlarla sınırlar.
  * `recur` – `:tree` formatındaki özyineleme işlemlerini kontrol eder. `:off` (varsayılan) ağacı normal olarak yazdırır. `:flat` bunun yerine herhangi bir özyinelemeyi (ip ile) sıkıştırır ve herhangi bir kendine özyinelemeyi bir yineleyiciye dönüştürmenin yaklaşık etkisini gösterir. `:flatc` aynı şeyi yapar ancak ayrıca C çerçevelerinin çökmesini de içerir (belirli durumlarda `jl_apply` etrafında garip şeyler yapabilir).
  * `threads::Union{Int,AbstractVector{Int}}` – Raporun hangi iş parçacıklarından anlık görüntüler içereceğini belirtir. Bunun, hangi iş parçacıklarında örneklerin toplandığını kontrol etmediğini unutmayın (bu örnekler başka bir makinede de toplanmış olabilir).
  * `tasks::Union{Int,AbstractVector{Int}}` – Raporun hangi görevlerden anlık görüntüler içereceğini belirtir. Bunun, hangi görevlerde örneklerin toplandığını kontrol etmediğini unutmayın.

!!! compat "Julia 1.8"
    `groupby`, `threads` ve `tasks` anahtar argümanları Julia 1.8'de tanıtılmıştır.


!!! note
    Windows'ta profil oluşturma ana iş parçacığı ile sınırlıdır. Diğer iş parçacıkları örneklenmemiştir ve raporda görünmeyecektir.

