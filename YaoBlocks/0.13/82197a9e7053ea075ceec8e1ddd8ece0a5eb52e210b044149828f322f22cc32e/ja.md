```
chain(blocks...) -> ChainBlock
chain(n) -> ChainBlock
```

同じ数のクディットを持つブロックのリストを連結する[`ChainBlock`](@ref)を返します。$G_i$をnクディットブロックの列とすると、ブロック`chain(G_1, G_2, ..., G_m)`の行列表現は次のようになります。

$$
G_m G_{m-1}\ldots G_1
$$

これは行列の乗算とほぼ同じですが、順序が逆になっています。量子回路はこの形でより自然に表現できるため、通常の行列乗算とは異なる順序にしています。

### 例

```jldoctest; setup=:(using Yao)
julia> chain(X, Y, Z)
nqubits: 1
chain
├─ X
├─ Y
└─ Z

julia> chain(2, put(1=>X), put(2=>Y), cnot(2, 1))
nqubits: 2
chain
├─ put on (1)
│  └─ X
├─ put on (2)
│  └─ Y
└─ control(2)
   └─ (1,) X
```
