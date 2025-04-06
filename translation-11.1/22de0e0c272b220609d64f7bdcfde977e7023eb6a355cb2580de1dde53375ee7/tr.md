```
restore(s::State, repo::GitRepo)
```

Bir `repo` deposunu, birleştirme denemesi öncesindeki bir dalın HEAD'i gibi, önceki bir `State` `s`'ye geri döndürür. `s`, [`snapshot`](@ref) fonksiyonu kullanılarak oluşturulabilir.
