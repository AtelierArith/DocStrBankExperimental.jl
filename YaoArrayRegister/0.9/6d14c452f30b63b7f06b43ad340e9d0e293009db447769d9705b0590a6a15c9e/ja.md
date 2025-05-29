```
arrayreg(state; nbatch::Union{Integer,NoBatch}=NoBatch(), nlevel::Integer=2)
```

配列レジスタを作成します。nbatchが整数の場合、`BatchedArrayReg`を返します。
