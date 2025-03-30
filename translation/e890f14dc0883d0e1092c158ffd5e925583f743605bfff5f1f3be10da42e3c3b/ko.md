```
copyto!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
        tM::AbstractChar,
        M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

행렬 `M`의 요소를 매개변수 `tM`에 따라 `B`로 효율적으로 복사합니다:

|  `tM` | 목적지                   | 출처                             |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `M[ir_src, jr_src]`            |
| `'T'` | `B[ir_dest, jr_dest]` | `transpose(M)[ir_src, jr_src]` |
| `'C'` | `B[ir_dest, jr_dest]` | `adjoint(M)[ir_src, jr_src]`   |

요소 `B[ir_dest, jr_dest]`는 덮어쓰여집니다. 또한, 인덱스 범위 매개변수는 `length(ir_dest) == length(ir_src)` 및 `length(jr_dest) == length(jr_src)`를 만족해야 합니다.

또한 [`copy_transpose!`](@ref) 및 [`copy_adjoint!`](@ref)를 참조하십시오.
