```
statevec(r::ArrayReg) -> array
```

最後のサイズ1の次元を削除することによって状態行列/ベクトルを返します（すなわち、`nactive(r) = nqudits(r)`）。[`state`](@ref)も参照してください。

!!! warning
    `statevec`は型安定ではありません。パフォーマンスの低下を引き起こす可能性があります。

