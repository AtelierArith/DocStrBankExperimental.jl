```
istaskfailed(t::Task) -> Bool
```

确定一个任务是否因为抛出异常而退出。

# 示例

```jldoctest
julia> a4() = error("任务失败");

julia> b = Task(a4);

julia> istaskfailed(b)
false

julia> schedule(b);

julia> yield();

julia> istaskfailed(b)
true
```

!!! compat "Julia 1.3"
    此函数至少需要 Julia 1.3。

