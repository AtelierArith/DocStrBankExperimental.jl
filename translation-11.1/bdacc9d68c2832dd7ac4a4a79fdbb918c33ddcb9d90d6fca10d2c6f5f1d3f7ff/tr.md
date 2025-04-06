```
gelsd!(A, B, rcond) -> (B, rnk)
```

`A * X = B` denkleminin en küçük norm çözümünü, `A`'nın `SVD` faktorizasyonunu bulup problemi bölerek çözer. `B`, çözüm `X` ile üzerine yazılır. `rcond`'un altındaki tekil değerler sıfır olarak kabul edilir. Çözümü `B`'de ve `A`'nın etkili sırasını `rnk`'de döner.
