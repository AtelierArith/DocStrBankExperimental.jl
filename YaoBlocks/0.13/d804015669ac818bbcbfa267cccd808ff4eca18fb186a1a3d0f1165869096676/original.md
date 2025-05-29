```
dump_gate(blk::AbstractBlock) -> Expr
```

convert a gate to a YaoScript expression for serization. The fallback is `GateTypeName(fields...)`
