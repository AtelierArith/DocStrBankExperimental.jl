```
operator_fidelity(b1::AbstractBlock, b2::AbstractBlock) -> Number
```

演算子の忠実度は次のように定義されます

$$
F(A, B) = \frac{1}{d}|{\rm Tr}(A^\dagger B)|
$$

ここで、`d`はヒルベルト空間のサイズです。この量はグローバル位相に依存しないことに注意してください。参照のために arXiv: 0803.2940v2 の式 (2) を見てください。

### 例

```jldoctest; setup=:(using Yao)
julia> operator_fidelity(X, X)
1.0

julia> operator_fidelity(X, Z)
0.0
```
