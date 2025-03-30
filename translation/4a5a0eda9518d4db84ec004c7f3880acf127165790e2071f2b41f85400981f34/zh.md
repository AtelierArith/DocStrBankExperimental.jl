```
RankDeficientException
```

当输入矩阵是 [秩缺陷](https://en.wikipedia.org/wiki/Rank_(linear_algebra)) 时抛出异常。一些线性代数函数，例如 Cholesky 分解，仅适用于非秩缺陷的矩阵。`info` 字段指示矩阵的计算秩。
