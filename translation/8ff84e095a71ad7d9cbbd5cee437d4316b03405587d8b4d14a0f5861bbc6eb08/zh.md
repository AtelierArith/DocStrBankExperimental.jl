```
fetch(c::RemoteChannel)
```

等待并从[`RemoteChannel`](@ref)获取一个值。引发的异常与[`Future`](@ref)相同。不会移除获取的项目。
