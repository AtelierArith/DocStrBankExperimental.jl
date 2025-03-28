```
keypress(m::AbstractMenu, i::UInt32) -> Bool
```

非標準のキー押下イベントを処理します。`true` が返されると、[`TerminalMenus.request`](@ref) は終了します。デフォルトは `false` です。
