```
ntuple(f, ::Val{N})
```

创建一个长度为 `N` 的元组，计算每个元素为 `f(i)`，其中 `i` 是元素的索引。通过传递 `Val(N)` 参数，这个版本的 ntuple 可能生成比将长度作为整数的版本更高效的代码。但是在 `N` 不能在编译时确定的情况下，`ntuple(f, N)` 比 `ntuple(f, Val(N))` 更可取。

# 示例

```jldoctest
julia> ntuple(i -> 2*i, Val(4))
(2, 4, 6, 8)
```
