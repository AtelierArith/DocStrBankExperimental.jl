```
bunchkaufman!(A, rook::Bool=false; check = true) -> BunchKaufman
```

`bunchkaufman!` 与 [`bunchkaufman`](@ref) 相同，但通过覆盖输入 `A` 来节省空间，而不是创建副本。
