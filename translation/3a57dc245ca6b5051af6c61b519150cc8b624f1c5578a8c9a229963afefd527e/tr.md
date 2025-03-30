```
transact(f::Function, repo::GitRepo)
```

Git deposu `repo` üzerinde `f` fonksiyonunu uygulayın, `f` uygulamadan önce bir [`snapshot`](@ref) alarak. Eğer `f` içinde bir hata oluşursa, `repo` snapshot durumuna geri dönecektir [`restore`](@ref) kullanılarak. Oluşan hata yeniden fırlatılacak, ancak `repo` durumu bozulmayacaktır.
