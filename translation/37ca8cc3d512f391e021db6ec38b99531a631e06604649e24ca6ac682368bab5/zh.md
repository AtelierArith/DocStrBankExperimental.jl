```
Base.identify_package(name::String)::Union{PkgId, Nothing}
Base.identify_package(where::Union{Module,PkgId}, name::String)::Union{PkgId, Nothing}
```

通过名称从当前环境栈中识别包，返回其 `PkgId`，如果找不到则返回 `nothing`。

如果只提供 `name` 参数，它会搜索栈中的每个环境及其命名的直接依赖项。

`where` 参数提供了搜索包的上下文：在这种情况下，它首先检查名称是否与上下文本身匹配，否则它会搜索所有递归依赖项（来自每个环境的已解析清单），直到找到上下文 `where`，然后从那里识别具有相应名称的依赖项。

```julia-repl
julia> Base.identify_package("Pkg") # Pkg 是默认环境的一个依赖项
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> using LinearAlgebra

julia> Base.identify_package(LinearAlgebra, "Pkg") # Pkg 不是 LinearAlgebra 的依赖项
```
