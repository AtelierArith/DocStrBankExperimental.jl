```
sparse!(I::AbstractVector{Ti}, J::AbstractVector{Ti}, V::AbstractVector{Tv},
        m::Integer, n::Integer, combine, klasttouch::Vector{Ti},
        csrrowptr::Vector{Ti}, csrcolval::Vector{Ti}, csrnzval::Vector{Tv},
        [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}] ) where {Tv,Ti<:Integer}
```

[`sparse`](@ref) 的父方法和专家驱动；有关基本用法，请参见 [`sparse`](@ref)。此方法允许用户为 `sparse` 的中间对象和结果提供预分配的存储，如下所述。此功能使得从坐标表示中更高效地连续构建 [`SparseMatrixCSC`](@ref)，并且还可以在没有额外成本的情况下提取结果转置的无序列表示。

此方法由三个主要步骤组成：（1）将提供的坐标表示计数排序为包含重复条目的无序行 CSR 形式。（2）遍历 CSR 形式，同时计算所需的 CSC 形式的列指针数组，检测重复条目，并将 CSR 形式中的重复条目重新打包；此阶段产生一个没有重复条目的无序行 CSR 形式。（3）将前面的 CSR 形式计数排序为一个完全排序的 CSC 形式，且没有重复条目。

输入数组 `csrrowptr`、`csrcolval` 和 `csrnzval` 构成中间 CSR 形式的存储，并要求 `length(csrrowptr) >= m + 1`、`length(csrcolval) >= length(I)` 和 `length(csrnzval >= length(I))`。输入数组 `klasttouch`，第二阶段的工作区，要求 `length(klasttouch) >= n`。可选输入数组 `csccolptr`、`cscrowval` 和 `cscnzval` 构成返回的 CSC 形式 `S` 的存储。如有必要，这些数组会自动调整大小以满足 `length(csccolptr) = n + 1`、`length(cscrowval) = nnz(S)` 和 `length(cscnzval) = nnz(S)`；因此，如果 `nnz(S)` 在开始时未知，传入适当类型的空向量（`Vector{Ti}()` 和 `Vector{Tv}()`）即可，或者调用 `sparse!` 方法时忽略 `cscrowval` 和 `cscnzval`。

返回时，`csrrowptr`、`csrcolval` 和 `csrnzval` 包含结果转置的无序列表示。

您可以重用输入数组的存储（`I`、`J`、`V`）用于输出数组（`csccolptr`、`cscrowval`、`cscnzval`）。例如，您可以调用 `sparse!(I, J, V, csrrowptr, csrcolval, csrnzval, I, J, V)`。请注意，它们将被调整大小以满足上述条件。

为了提高效率，此方法在 `1 <= I[k] <= m` 和 `1 <= J[k] <= n` 之外不执行参数检查。请谨慎使用。使用 `--check-bounds=yes` 进行测试是明智的。

此方法的运行时间为 `O(m, n, length(I))`。F. Gustavson 在其论文 "Two fast algorithms for sparse matrices: multiplication and permuted transposition," ACM TOMS 4(3), 250-269 (1978) 中描述的 HALFPERM 算法启发了此方法使用一对计数排序。
