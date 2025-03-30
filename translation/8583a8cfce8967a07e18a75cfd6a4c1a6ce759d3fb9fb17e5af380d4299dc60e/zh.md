```
merge(a::NamedTuple, iterable)
```

将键值对的可迭代对象解释为命名元组，并执行合并。

```jldoctest
julia> merge((a=1, b=2, c=3), [:b=>4, :d=>5])
(a = 1, b = 4, c = 3, d = 5)
```
