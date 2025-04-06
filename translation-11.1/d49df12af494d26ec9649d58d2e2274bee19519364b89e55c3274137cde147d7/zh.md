```
countfrom(start=1, step=1)
```

一个从 `start` 开始并以 `step` 递增的无限计数迭代器。

# 示例

```jldoctest
julia> for v in Iterators.countfrom(5, 2)
           v > 10 && break
           println(v)
       end
5
7
9
```
