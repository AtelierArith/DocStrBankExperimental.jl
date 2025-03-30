```
close(c::Channel[, excp::Exception])
```

关闭一个通道。一个异常（可选地由 `excp` 给出）会在以下情况下抛出：

  * 在一个已关闭的通道上使用 [`put!`](@ref)。
  * 在一个空的、已关闭的通道上使用 [`take!`](@ref) 和 [`fetch`](@ref)。
