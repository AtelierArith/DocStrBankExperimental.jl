```
TaskLocalRNG
```

`TaskLocalRNG`, görevi için yerel olan bir duruma sahiptir, ipliği için değil. Görev oluşturulurken, ana görevin durumundan tohumlanır, ancak ana görevin RNG'sinin durumunu ilerletmeden.

Bir avantaj olarak, `TaskLocalRNG` oldukça hızlıdır ve yarış koşulları hariç, zamanlayıcı kararlarından bağımsız olarak yeniden üretilebilir çok iş parçacıklı simülasyonlara izin verir. Görev oluşturma kararlarında iş parçacığı sayısı kullanılmadığı sürece, simülasyon sonuçları mevcut iş parçacığı / CPU sayısından da bağımsızdır. Rastgele akış, donanım ayrıntılarına bağlı olmamalıdır, sonlandırma ve muhtemelen kelime boyutu hariç.

`current_task()` tarafından döndürülen görevden başka bir görevin RNG'sini kullanmak veya tohumlamak tanımsız bir davranıştır: çoğu zaman çalışır ve bazen sessizce başarısız olabilir.

`TaskLocalRNG()`'yi [`seed!`](@ref) ile tohumlarken, geçirilen tohum, varsa, herhangi bir tam sayı olabilir.

!!! compat "Julia 1.11"
    Negatif bir tam sayı tohumu ile `TaskLocalRNG()`'yi tohumlamak en az Julia 1.11 gerektirir.


!!! compat "Julia 1.10"
    Görev oluşturma, Julia 1.10 itibarıyla ana görevin RNG durumunu ilerletmez.

