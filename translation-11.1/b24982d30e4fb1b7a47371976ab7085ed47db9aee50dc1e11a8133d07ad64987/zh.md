```
nameof(t::DataType) -> Symbol
```

获取（可能被 `UnionAll` 包裹的）`DataType` 的名称（不包括其父模块），作为符号。

# 示例

```jldoctest
julia> module Foo
           struct S{T}
           end
       end
Foo

julia> nameof(Foo.S{T} where T)
:S
```
