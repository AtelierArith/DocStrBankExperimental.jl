```
dump_gate(blk::AbstractBlock) -> Expr
```

ゲートをシリアライズのためのYaoScript式に変換します。フォールバックは `GateTypeName(fields...)` です。
