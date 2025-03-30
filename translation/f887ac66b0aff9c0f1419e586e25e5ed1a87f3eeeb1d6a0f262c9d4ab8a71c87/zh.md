```
ispublic(m::Module, s::Symbol) -> Bool
```

返回一个符号在模块中是否被标记为公共。

导出的符号被视为公共。

!!! compat "Julia 1.11"
    此函数和公共性的概念是在 Julia 1.11 中添加的。


另请参见: [`isexported`](@ref), [`names`](@ref)

```jldoctest
julia> module Mod
           export foo
           public bar
       end
Mod

julia> Base.ispublic(Mod, :foo)
true

julia> Base.ispublic(Mod, :bar)
true

julia> Base.ispublic(Mod, :baz)
false
```
