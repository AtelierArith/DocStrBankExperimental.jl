```
select!(dest::AbstractRegister, src::AbstractRegister, bits::Integer...) -> AbstractRegister
select!(register::AbstractRegister, bits::Integer...) -> register
```

入力固有状態 `bits` に基づいて、与えられた量子状態のサブスペースを選択します。詳細は [`select`](@ref) を参照してください。

## 例

`select!(reg, 0b110)` は、(フォーカスされた) 構成 `110` を持つサブスペースを選択します。選択後、フォーカスされたキュービット空間は 0 になるため、手動で `relax!` を呼び出すことをお勧めします。

!!! tip
    開発者は `select!(r::RegisterType, bits::NTuple{N, <:Integer})` をオーバーロードすべきであり、`bits` が特定のビット数 (例: `Int64`) を持つと仮定すべきではありません。そうしないと、利用可能な最大のキュディット数が制限されます。

