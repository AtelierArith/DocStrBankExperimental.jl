```
zbarimg(; adjust_PATH::Bool=true, adjust_LIBPATH::Bool=true) -> Cmd
```

zbarimgの実行をサポートする`ExecutableProduct`ラッパーです。このラッパーはスレッドセーフであり、Julia 1.6以上ではこちらを推奨します。

# 例

```julia
run(`$(zbarimg()) $arguments`)
```

!!! compat "Julia 1.6"
    このメソッドはJuliaバージョン1.6以上を必要とします。

