```
reset(::Event)
```

将[`Event`](@ref)重置为未设置状态。然后，任何未来对`wait`的调用将会阻塞，直到再次调用[`notify`](@ref)。
