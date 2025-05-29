```
operator_fidelity(b1::AbstractBlock, b2::AbstractBlock) -> Number
```

演算子の忠実度は次のように定義されます

$$
F^2 = \frac{1}{d^2}\left[{\rm Tr}(b1^\dagger b2)\right]
$$

ここで、`d`はヒルベルト空間のサイズです。この量はグローバル位相に依存しないことに注意してください。参照のために arXiv: 0803.2940v2 の式 (2) を見てください。
