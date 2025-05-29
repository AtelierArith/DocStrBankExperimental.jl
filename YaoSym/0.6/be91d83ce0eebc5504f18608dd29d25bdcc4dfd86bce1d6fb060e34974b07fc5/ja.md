```
@bra_str
```

ブラレジスタを作成します。詳細は [`@ket_str`](@ref) を参照してください。

### 例

`@ket_str` リテラルと同様に、記号的な量子状態は次のように作成できます。

```jldoctest; setup=:(using Yao)
julia> bra"111" + 2bra"101"
2.0⟨101| + ⟨111|

julia> bra"111" * (ket"101" + ket"111")
1
```
