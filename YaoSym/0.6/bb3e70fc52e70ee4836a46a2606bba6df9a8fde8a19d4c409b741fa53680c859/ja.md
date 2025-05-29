```
@ket_str
```

ケトレジスタを作成します。詳細は[`@bra_str`](@ref)を参照してください。

### 例

記号的な量子状態は、単純に次のように作成できます。

```jldoctest; setup=:(using Yao)
julia> ket"110" + 2ket"111"
|110⟩ + 2.0|111⟩
```

キュービットは[`focus!`](@ref)によって部分的にアクティブにすることができます。

```jldoctest; setup=:(using Yao)
julia> ket"100" + ket"111" |> focus!(1:2)
|100⟩ + |111⟩
```
