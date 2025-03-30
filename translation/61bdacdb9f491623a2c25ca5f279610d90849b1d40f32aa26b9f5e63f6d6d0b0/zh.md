```
copy_transpose!(B::AbstractVecOrMat, ir_dest::AbstractRange{Int}, jr_dest::AbstractRange{Int},
                A::AbstractVecOrMat, ir_src::AbstractRange{Int}, jr_src::AbstractRange{Int}) -> B
```

高效地将矩阵 `A` 的元素复制到 `B`，并进行转置，如下所示：

```
B[ir_dest, jr_dest] = transpose(A)[jr_src, ir_src]
```

元素 `B[ir_dest, jr_dest]` 会被覆盖。此外，索引范围参数必须满足 `length(ir_dest) == length(jr_src)` 和 `length(jr_dest) == length(ir_src)`。
