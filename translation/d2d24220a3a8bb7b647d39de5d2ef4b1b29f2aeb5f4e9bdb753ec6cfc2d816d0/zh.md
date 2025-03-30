```
unmark(s::IO)
```

从流 `s` 中移除标记。如果流被标记，则返回 `true`，否则返回 `false`。

另见 [`mark`](@ref), [`reset`](@ref), [`ismarked`](@ref).
