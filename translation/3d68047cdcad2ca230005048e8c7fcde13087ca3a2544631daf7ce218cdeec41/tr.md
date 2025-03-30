```
ReentrantLock()
```

Bir [`Task`](@ref) senkronizasyonu için yeniden giriş kilidi oluşturur. Aynı görev, gerektiği kadar kilidi alabilir (bu, adın "Yeniden Giriş" kısmının anlamıdır). Her [`lock`](@ref) bir [`unlock`](@ref) ile eşleşmelidir.

`lock` çağrısı, ilgili `unlock`'a kadar o iş parçacığında sonlandırıcıların çalışmasını da engelleyecektir. Aşağıda gösterilen standart kilit deseninin doğal olarak desteklenmesi gerekir, ancak deneme/kilit sırasını tersine çevirmekten veya deneme bloğunu tamamen atlamaktan (örneğin, kilit hala tutulurken geri dönmeye çalışmak) kaçının:

Bu, kilit/açma çağrıları üzerinde bir alma/serbest bırakma bellek sıralaması sağlar.

```
lock(l)
try
    <atomik iş>
finally
    unlock(l)
end
```

Eğer [`!islocked(lck::ReentrantLock)`](@ref islocked) geçerliyse, [`trylock(lck)`](@ref trylock) başarılı olur, aksi takdirde kilidi "aynı anda" tutmaya çalışan başka görevler varsa başarısız olur.
