```
lu(A::AbstractSparseMatrixCSC; check = true, q = nothing, control = get_umfpack_control()) -> F::UmfpackLU
```

计算稀疏矩阵 `A` 的 LU 分解。

对于元素类型为实数或复数的稀疏 `A`，返回类型 `F` 为 `UmfpackLU{Tv, Ti}`，其中 `Tv` = [`Float64`](@ref) 或 `ComplexF64`，而 `Ti` 是整数类型（[`Int32`](@ref) 或 [`Int64`](@ref)）。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）由用户承担。

置换 `q` 可以是一个置换向量或 `nothing`。如果未提供置换向量或 `q` 为 `nothing`，则使用 UMFPACK 的默认值。如果置换不是零基的，则会制作一个零基的副本。

`control` 向量默认为 Julia SparseArrays 包的 UMFPACK 默认配置（注意：这已从 UMFPACK 默认值修改，以禁用迭代精炼），但可以通过传递长度为 `UMFPACK_CONTROL` 的向量进行更改，具体配置请参见 UMFPACK 手册。例如，要重新启用迭代精炼：

```
umfpack_control = SparseArrays.UMFPACK.get_umfpack_control(Float64, Int64) # 读取 Float64 稀疏矩阵的 Julia 默认配置
SparseArrays.UMFPACK.show_umf_ctrl(umfpack_control) # 可选 - 显示值
umfpack_control[SparseArrays.UMFPACK.JL_UMFPACK_IRSTEP] = 2.0 # 重新启用迭代精炼（2 是 UMFPACK 默认的最大迭代精炼步骤）

Alu = lu(A; control = umfpack_control)
x = Alu \ b   # 解 Ax = b，包括 UMFPACK 迭代精炼
```

可以通过索引访问分解 `F` 的各个组件：

| 组件   | 描述                |
|:---- |:----------------- |
| `L`  | `LU` 的 `L`（下三角）部分 |
| `U`  | `LU` 的 `U`（上三角）部分 |
| `p`  | 右置换 `Vector`      |
| `q`  | 左置换 `Vector`      |
| `Rs` | 缩放因子的 `Vector`    |
| `:`  | `(L,U,p,q,Rs)` 组件 |

`F` 和 `A` 之间的关系为

`F.L*F.U == (F.Rs .* A)[F.p, F.q]`

`F` 进一步支持以下函数：

  * [`\`](@ref)
  * [`det`](@ref)

另见 [`lu!`](@ref)

!!! note
    `lu(A::AbstractSparseMatrixCSC)` 使用的是 UMFPACK[^ACM832] 库，该库是 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) 的一部分。由于该库仅支持元素为 [`Float64`](@ref) 或 `ComplexF64` 的稀疏矩阵，`lu` 会将 `A` 转换为类型为 `SparseMatrixCSC{Float64}` 或 `SparseMatrixCSC{ComplexF64}` 的副本。


[^ACM832]: Davis, Timothy A. (2004b). Algorithm 832: UMFPACK V4.3–-an Unsymmetric-Pattern Multifrontal Method. ACM Trans. Math. Softw., 30(2), 196–199. [doi:10.1145/992200.992206](https://doi.org/10.1145/992200.992206)
