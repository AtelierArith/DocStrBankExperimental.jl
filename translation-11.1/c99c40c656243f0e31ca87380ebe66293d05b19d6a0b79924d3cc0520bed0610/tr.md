```
wait([x])
```

Mevcut görevi, argümanın türüne bağlı olarak bir olay meydana gelene kadar engeller:

  * [`Channel`](@ref): Kanalda bir değerin eklenmesini bekleyin.
  * [`Condition`](@ref): Bir koşulda [`notify`](@ref) için bekleyin ve `notify`'ye geçirilen `val` parametresini döndürün. Bir koşulda beklemek, ayrıca `first=true` geçişine izin verir; bu, bekleyenin `notify` üzerinde uyanmak için sıranın *ilk* sırasına yerleştirilmesiyle sonuçlanır, bu da genellikle ilk giren ilk çıkar davranışıdır.
  * `Process`: Bir işlemin veya işlem zincirinin çıkmasını bekleyin. Bir işlemin `exitcode` alanı, başarı veya başarısızlığı belirlemek için kullanılabilir.
  * [`Task`](@ref): Bir `Task`'ın bitmesini bekleyin. Eğer görev bir istisna ile başarısız olursa, bir `TaskFailedException` (başarısız olan görevi saran) fırlatılır.
  * [`RawFD`](@ref): Bir dosya tanımlayıcısındaki değişiklikleri bekleyin (bkz. `FileWatching` paketi).

Hiçbir argüman geçilmezse, görev belirsiz bir süre engellenir. Bir görev yalnızca [`schedule`](@ref) veya [`yieldto`](@ref) için açık bir çağrı ile yeniden başlatılabilir.

Genellikle `wait`, beklenen bir koşulun karşılandığından emin olmak için bir `while` döngüsü içinde çağrılır.
