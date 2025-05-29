```
datatype(register) -> Int
```

registerによって使用される数値データ型を返します。

!!! note
    `datatype`は`eltype`とは異なります。なぜなら、`AbstractRegister`ファミリーは`AbstractArray`とは正確には同じではなく、いくつかのレジスタのイテレータだからです。

