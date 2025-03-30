```
permutedims!(dest, src, perm)
```

对数组 `src` 的维度进行排列，并将结果存储在数组 `dest` 中。`perm` 是一个指定长度为 `ndims(src)` 的排列向量。预分配的数组 `dest` 应该满足 `size(dest) == size(src)[perm]`，并且会被完全覆盖。不支持就地排列，如果 `src` 和 `dest` 有重叠的内存区域，将会出现意外结果。

另见 [`permutedims`](@ref).
