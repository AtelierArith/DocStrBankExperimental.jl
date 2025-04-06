# Module loading

[`Base.require`](@ref) 负责加载模块，并且管理预编译缓存。它是 `import` 语句的实现。

## Experimental features

以下功能是实验性的，不属于稳定的 Julia API。在基于它们进行开发之前，请了解当前的思路以及它们是否可能很快发生变化。

### Package loading callbacks

可以通过注册回调来监听 `Base.require` 加载的包。

```julia
loaded_packages = Base.PkgId[]
callback = (pkg::Base.PkgId) -> push!(loaded_packages, pkg)
push!(Base.package_callbacks, callback)
```

使用这个看起来会像这样：

```julia-repl
julia> using Example

julia> loaded_packages
1-element Vector{Base.PkgId}:
 Example [7876af07-990d-54b4-ab0e-23690620f79a]
```
