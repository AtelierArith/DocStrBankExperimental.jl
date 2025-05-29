```
reorder!(reigster, orders)
```

入力されたオーダーによってレジスタの位置を再配置します。3量子ビットのレジスタに対して、オーダー `(i, j, k)` は次の量子ビットの再配置を指定します。

  * 最初の量子ビットを `i` に移動します。
  * 2番目の量子ビットを `j` に移動します。
  * 3番目の量子ビットを `k` に移動します。

!!! note
    `reorder!` の規約は `permutedims` 関数とは異なります。`sortperm` 関数を使用して、置換オーダーとこの関数のオーダーを関連付けることができます。


### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"010101");

julia> reorder!(reg, (1,4,2,5,3,6));

julia> measure(reg)
1-element Vector{DitStr{2, 6, Int64}}:
 000111 ₍₂₎
```
