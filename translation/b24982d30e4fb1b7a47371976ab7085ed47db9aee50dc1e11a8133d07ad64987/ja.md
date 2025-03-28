```
nameof(t::DataType) -> Symbol
```

`DataType`（親モジュールなし）の名前をシンボルとして取得します（`UnionAll`でラップされている可能性があります）。

# 例

```jldoctest
julia> module Foo
           struct S{T}
           end
       end
Foo

julia> nameof(Foo.S{T} where T)
:S
```
