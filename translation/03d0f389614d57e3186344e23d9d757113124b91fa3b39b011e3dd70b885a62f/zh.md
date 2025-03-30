```
find_library(names [, locations])
```

在 `locations` 列表中的路径、`DL_LOAD_PATH` 或系统库路径中（按此顺序）搜索 `names` 中的第一个库，该库可以成功地被 dlopen。成功时，返回值将是 `names` 中的一个（可能以 `locations` 中的一个路径为前缀）。这个字符串可以被赋值给一个 `global const`，并在未来的 `ccall` 中用作库名称。失败时，它返回空字符串。
