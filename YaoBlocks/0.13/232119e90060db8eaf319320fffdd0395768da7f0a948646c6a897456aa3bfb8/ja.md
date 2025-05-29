```
kron(n, locs_and_blocks::Pair{<:Any, <:AbstractBlock}...) -> KronBlock
```

`n`-量子ビット [`KronBlock`](@ref) を返します。入力は、位置とブロックのペアのリストを含み、位置は整数または範囲であることができます。これは、アドレスの競合がない [`put`](@ref) ブロックの概念的な [`chain`](@ref) ですが、さまざまな目的に役立つより豊富な型情報を持っています。たとえば、より効率的な [`mat`](@ref) 関数などです。

$$
I
$$

を $2\times 2$ 単位行列、$G$ と $H$ を2つの $2\times 2$ 行列とすると、`kron(n, i=>G, j=>H)` の行列表現（$j > i$ と仮定）は次のように定義されます。

$$
I^{\otimes n-j} \otimes H \otimes I^{\otimes j-i-1} \otimes G \otimes I^{i-1}
$$

複数の位置の場合、式は複雑になることがあります。

### 例

`kron` を使用して `KronBlock` を構築すると、`1` 番目の量子ビットに `X` ゲートを、`3` 番目の量子ビットに `Y` ゲートを配置します。

```jldoctest; setup=:(using Yao)
julia> kron(4, 1=>X, 3=>Y)
nqubits: 4
kron
├─ 1=>X
└─ 3=>Y
```
