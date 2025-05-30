```
reorder!(reigster, orders)
```

入力されたオーダーによってレジスタの位置を再配置します。3量子ビットのレジスタに対して、オーダー `(i, j, k)` は次の量子ビットの再配置を指定します。

  * 最初の量子ビットを `i` に移動する、
  * 2番目の量子ビットを `j` に移動する、
  * 3番目の量子ビットを `k` に移動する。

!!! note
    `reorder!` の規約は `permutedims` 関数とは異なり、`sortperm` 関数を使用して置換順序とこの関数の順序を関連付けることができます。


### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"010101");

julia> reorder!(reg, (1,4,2,5,3,6));

julia> measure(reg)
1-element Vector{DitStr{2, 6, Int64}}:
 000111 ₍₂₎
```
