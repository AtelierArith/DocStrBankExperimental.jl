```
pkgdir(m::Module[, paths::String...])
```

返回声明模块 `m` 的包的根目录，如果 `m` 不是在包中声明的，则返回 `nothing`。可以选择提供更多路径组件字符串，以在包根目录内构造路径。

要获取实现当前模块的包的根目录，可以使用形式 `pkgdir(@__MODULE__)`。

如果给定的是扩展模块，则返回父包的根目录。

```julia-repl
julia> pkgdir(Foo)
"/path/to/Foo.jl"

julia> pkgdir(Foo, "src", "file.jl")
"/path/to/Foo.jl/src/file.jl"
```

另见 [`pathof`](@ref)。

!!! compat "Julia 1.7"
    可选参数 `paths` 至少需要 Julia 1.7。

