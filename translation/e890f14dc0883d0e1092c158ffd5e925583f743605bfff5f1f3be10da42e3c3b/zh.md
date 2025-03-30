```
copyto!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
        tM::AbstractChar,
        M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

高效地将矩阵 `M` 的元素复制到 `B`，条件是字符参数 `tM` 如下：

|  `tM` | 目标                    | 源                              |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `M[ir_src, jr_src]`            |
| `'T'` | `B[ir_dest, jr_dest]` | `transpose(M)[ir_src, jr_src]` |
| `'C'` | `B[ir_dest, jr_dest]` | `adjoint(M)[ir_src, jr_src]`   |

元素 `B[ir_dest, jr_dest]` 会被覆盖。此外，索引范围参数必须满足 `length(ir_dest) == length(ir_src)` 和 `length(jr_dest) == length(jr_src)`。

另见 [`copy_transpose!`](@ref) 和 [`copy_adjoint!`](@ref)。
