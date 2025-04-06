```
Base.locate_package(pkg::PkgId)::Union{String, Nothing}
```

对应于标识符 `pkg` 的包的入口文件路径，如果未找到则返回 `nothing`。另见 [`identify_package`](@ref)。

```julia-repl
julia> pkg = Base.identify_package("Pkg")
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> Base.locate_package(pkg)
"/path/to/julia/stdlib/v1.11/Pkg/src/Pkg.jl"
```
