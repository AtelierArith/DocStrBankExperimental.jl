```
reset(s::IO)
```

将流 `s` 重置为先前标记的位置，并移除标记。返回先前标记的位置。如果流未标记，则抛出错误。

另请参见 [`mark`](@ref), [`unmark`](@ref), [`ismarked`](@ref).
