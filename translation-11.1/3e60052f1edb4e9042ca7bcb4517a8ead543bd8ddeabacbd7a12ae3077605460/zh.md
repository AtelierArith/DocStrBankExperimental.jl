```
filter!(f, a)
```

更新集合 `a`，移除 `f` 返回 `false` 的元素。函数 `f` 接受一个参数。

# 示例

```jldoctest
julia> filter!(isodd, Vector(1:10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
