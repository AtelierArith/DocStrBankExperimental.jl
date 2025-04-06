```
LibGit2.status(repo::GitRepo, path::String) -> Union{Cuint, Cvoid}
```

`repo` içindeki `path`'teki dosyanın durumunu kontrol edin. Örneğin, bu, `path`'teki dosyanın değiştirilip değiştirilmediğini ve sahneye alınması ve taahhüt edilmesi gerekip gerekmediğini kontrol etmek için kullanılabilir.
