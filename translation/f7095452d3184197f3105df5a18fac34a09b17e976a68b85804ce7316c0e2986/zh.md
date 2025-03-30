```
similar(storagetype, axes)
```

创建一个未初始化的可变数组，类似于由 `storagetype` 指定的数组，但其维度由最后一个参数 `axes` 指定。

**示例**：

```
similar(Array{Int}, axes(A))
```

创建一个“像” `Array{Int}` 的数组（并且可能确实由一个支持），但其索引与 `A` 相同。如果 `A` 具有常规索引，这将与 `Array{Int}(undef, size(A))` 相同，但如果 `A` 具有非常规索引，则结果的索引将与 `A` 匹配。

```
similar(BitArray, (axes(A, 2),))
```

将创建一个一维逻辑数组，其索引与 `A` 的列相匹配。
