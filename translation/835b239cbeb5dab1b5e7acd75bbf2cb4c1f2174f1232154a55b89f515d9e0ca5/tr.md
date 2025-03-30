```
exit_on_sigint(on::Bool)
```

Julia çalışma zamanının `exit_on_sigint` bayrağını ayarlar. Eğer `false` ise, Ctrl-C (SIGINT) `try` bloğunda [`InterruptException`](@ref) olarak yakalanabilir. Bu, REPL'deki varsayılan davranıştır, `-e` ve `-E` ile çalıştırılan herhangi bir kodda ve `-i` seçeneği ile çalıştırılan Julia betiğinde geçerlidir.

Eğer `true` ise, Ctrl-C tarafından `InterruptException` fırlatılmaz. Böyle bir olay üzerine kod çalıştırmak [`atexit`](@ref) gerektirir. Bu, `-i` seçeneği olmadan çalıştırılan Julia betiğinde varsayılan davranıştır.

!!! compat "Julia 1.5"
    `exit_on_sigint` fonksiyonu en az Julia 1.5 gerektirir.

