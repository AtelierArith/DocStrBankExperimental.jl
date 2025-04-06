```
InterruptException()
```

Süreç bir terminal kesintisi (CTRL+C) ile durduruldu.

Not edin ki, `-i` (etkileşimli) seçeneği olmadan başlatılan Julia betiğinde, `InterruptException` varsayılan olarak atılmaz. Betikte [`Base.exit_on_sigint(false)`](@ref Base.exit_on_sigint) çağrısı, REPL'in davranışını geri kazanabilir. Alternatif olarak, bir Julia betiği şu şekilde başlatılabilir:

```sh
julia -e "include(popfirst!(ARGS))" script.jl
```

CTRL+C sırasında yürütme sırasında `InterruptException` atılmasına izin vermek için.
