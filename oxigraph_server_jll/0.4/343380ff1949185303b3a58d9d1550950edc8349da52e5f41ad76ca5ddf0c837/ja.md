```
oxigraph_server(f::Function; adjust_PATH::Bool=true, adjust_LIBPATH::Bool=true)
```

`ExecutableProduct` ラッパーで、oxigraph_server の実行をサポートします。

!!! warning "非推奨"
    このメソッドはスレッドセーフではないため非推奨であり、将来の Julia バージョンで削除されます。代わりに非 do ブロック形式を使用してください。


# 例

```julia
oxigraph_server() do exe
    run(`$exe $arguments`)
end
```

!!! compat "Julia 1.3"
    このメソッドは Julia バージョン 1.3 以降を必要とします。

