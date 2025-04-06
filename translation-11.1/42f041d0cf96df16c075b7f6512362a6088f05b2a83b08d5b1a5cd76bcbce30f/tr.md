```
SpinLock()
```

Reentransız, test-et-test-et-ve-kur kilidi oluşturun. Rekürsif kullanım bir ölü kilitlenmeye yol açacaktır. Bu tür bir kilit, yalnızca kısa sürede çalıştırılan ve engellemeyen (örneğin, I/O gerçekleştiren) kod etrafında kullanılmalıdır. Genel olarak, [`ReentrantLock`](@ref) bunun yerine kullanılmalıdır.

Her [`lock`](@ref) bir [`unlock`](@ref) ile eşleştirilmelidir. Eğer [`!islocked(lck::SpinLock)`](@ref islocked) geçerliyse, [`trylock(lck)`](@ref trylock) başarılı olur, aksi takdirde kilidi "aynı anda" tutmaya çalışan başka görevler varsa başarısız olur.

Test-et-test-et-ve-kur spin kilitleri, yaklaşık 30 civarında rekabet eden iş parçacığına kadar en hızlıdır. Eğer bundan daha fazla rekabet varsa, farklı senkronizasyon yaklaşımları düşünülmelidir.
