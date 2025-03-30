```
@kwdef typedef
```

这是一个辅助宏，它自动为在表达式 `typedef` 中声明的类型定义基于关键字的构造函数，该类型必须是 `struct` 或 `mutable struct` 表达式。默认参数通过声明形式为 `field::T = default` 或 `field = default` 的字段来提供。如果没有提供默认值，则关键字参数在生成的类型构造函数中变为必需的关键字参数。

内部构造函数仍然可以定义，但至少一个应该接受与默认内部构造函数相同形式的参数（即每个字段一个位置参数），以便与关键字外部构造函数正确配合使用。

!!! compat "Julia 1.1"
    对于参数化结构体和具有超类型的结构体，`Base.@kwdef` 至少需要 Julia 1.1。


!!! compat "Julia 1.9"
    从 Julia 1.9 开始，该宏被导出。


# 示例

```jldoctest
julia> @kwdef struct Foo
           a::Int = 1         # 指定的默认值
           b::String          # 必需的关键字
       end
Foo

julia> Foo(b="hi")
Foo(1, "hi")

julia> Foo()
ERROR: UndefKeywordError: 关键字参数 `b` 未分配
Stacktrace:
[...]
```
