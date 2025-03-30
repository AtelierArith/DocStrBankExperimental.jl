```
isready(rr::RemoteChannel, args...)
```

确定一个 [`RemoteChannel`](@ref) 是否存储了一个值。请注意，这个函数可能会导致竞争条件，因为在你收到结果时，它可能不再成立。然而，它可以安全地用于 [`Future`](@ref)，因为它们只被赋值一次。
