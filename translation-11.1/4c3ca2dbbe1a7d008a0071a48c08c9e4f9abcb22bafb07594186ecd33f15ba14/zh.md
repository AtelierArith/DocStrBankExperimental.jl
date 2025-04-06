```
parentmodule(t::DataType) -> Module
```

确定包含（可能被 `UnionAll` 包裹的）`DataType` 定义的模块。

# 示例

```jldoctest
julia> module Foo
           struct Int end
       end
Foo

julia> parentmodule(Int)
Core

julia> parentmodule(Foo.Int)
Foo
```
