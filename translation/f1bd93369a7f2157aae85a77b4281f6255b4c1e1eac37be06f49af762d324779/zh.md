```
istaskstarted(t::Task) -> Bool
```

确定任务是否已开始执行。

# 示例

```jldoctest
julia> a3() = sum(i for i in 1:1000);

julia> b = Task(a3);

julia> istaskstarted(b)
false
```
