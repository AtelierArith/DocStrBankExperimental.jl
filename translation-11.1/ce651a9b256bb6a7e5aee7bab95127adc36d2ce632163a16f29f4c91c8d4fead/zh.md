```
ldlt!(F::CHOLMOD.Factor, A::SparseMatrixCSC; shift = 0.0, check = true) -> CHOLMOD.Factor
```

计算 `A` 的 $LDL'$ 分解，重用符号分解 `F`。`A` 必须是 [`SparseMatrixCSC`](@ref) 或 `SparseMatrixCSC` 的 [`Symmetric`](@ref)/[`Hermitian`](@ref) 视图。请注意，即使 `A` 没有类型标签，它仍必须是对称的或厄米的。

另请参见 [`ldlt`](@ref)。

!!! note
    此方法使用来自 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) 的 CHOLMOD 库，仅支持单精度或双精度的实数或复数类型。输入矩阵如果不是这些元素类型，将会被适当地转换为这些类型。

