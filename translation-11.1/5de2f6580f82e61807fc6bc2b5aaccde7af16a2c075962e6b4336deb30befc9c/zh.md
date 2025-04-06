```
pathof(m::Module)
```

返回用于 `import` 模块 `m` 的 `m.jl` 文件的路径，如果 `m` 不是从包中导入的，则返回 `nothing`。

使用 [`dirname`](@ref) 获取路径的目录部分，使用 [`basename`](@ref) 获取文件名部分。

另见 [`pkgdir`](@ref)。
