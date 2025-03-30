```
snapshot(repo::GitRepo) -> State
```

Mevcut `repo` deposunun durumunun bir anlık görüntüsünü alır, mevcut HEAD'i, dizini ve herhangi bir taahhüt edilmemiş çalışmayı saklar. Çıktı `State`, daha sonra [`restore`](@ref) çağrısında kullanılarak deponun anlık görüntülenen duruma geri döndürülmesi için kullanılabilir.
