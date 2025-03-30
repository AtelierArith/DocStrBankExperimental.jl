```
timedwait(testcb, timeout::Real; pollint::Real=0.1)
```

等待直到 `testcb()` 返回 `true` 或者超时 `timeout` 秒，以先到者为准。测试函数每 `pollint` 秒被轮询一次。`pollint` 的最小值为 0.001 秒，即 1 毫秒。

返回 `:ok` 或 `:timed_out`。

# 示例

```jldoctest
julia> cb() = (sleep(5); return);

julia> t = @async cb();

julia> timedwait(()->istaskdone(t), 1)
:timed_out

julia> timedwait(()->istaskdone(t), 6.5)
:ok
```
