```
redirect_stdout([stream]) -> stream
```

Tüm C ve Julia düzeyindeki [`stdout`](@ref) çıktısının yönlendirileceği bir boru oluşturur. Boru uçlarını temsil eden bir akış döndürür. [`stdout`](@ref) üzerine yazılan veriler artık borunun `rd` ucundan okunabilir.

!!! not
    `stream` uyumlu bir nesne olmalıdır, örneğin bir `IOStream`, `TTY`, [`Pipe`](@ref), soket veya `devnull`.


Ayrıca bkz. [`redirect_stdio`](@ref).
