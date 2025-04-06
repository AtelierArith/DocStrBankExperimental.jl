```
disable_sigint(f::Function)
```

Bir işlevin yürütülmesi sırasında Ctrl-C işleyicisini devre dışı bırakır, dış kod çağırmak için, bu kodun kesinti güvenli olmayan julia kodunu çağırabileceği durumlar için. Aşağıdaki gibi `do` blok sözdizimi kullanılarak çağrılması amaçlanmıştır:

```
disable_sigint() do
    # kesinti güvenli olmayan kod
    ...
end
```

Bu, işçi iş parçacıklarında (`Threads.threadid() != 1`) gerekli değildir, çünkü `InterruptException` yalnızca ana iş parçacığına iletilecektir. Julia kodunu veya julia çalışma zamanını çağırmayan dış işlevler, yürütmeleri sırasında otomatik olarak sigint'i devre dışı bırakır.
