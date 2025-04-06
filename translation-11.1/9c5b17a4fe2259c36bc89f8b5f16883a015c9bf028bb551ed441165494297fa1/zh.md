```
getri!(A, ipiv)
```

计算 `A` 的逆，使用通过 `getrf!` 找到的 `LU` 分解。`ipiv` 是输出的主元信息，`A` 包含 `getrf!` 的 `LU` 分解。`A` 被覆盖为其逆。
