```
oxigraph_server(; adjust_PATH::Bool=true, adjust_LIBPATH::Bool=true) -> Cmd
```

`ExecutableProduct` ラッパーで、oxigraph_server の実行をサポートします。このラッパーはスレッドセーフであり、Julia 1.6 以上では推奨されます。

# 例

```julia
run(`$(oxigraph_server()) $arguments`)
```

!!! compat "Julia 1.6"
    このメソッドは Julia バージョン 1.6 以上を必要とします。

