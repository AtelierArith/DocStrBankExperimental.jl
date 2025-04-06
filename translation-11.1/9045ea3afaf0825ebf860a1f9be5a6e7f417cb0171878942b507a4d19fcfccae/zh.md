```
模块
```

`module` 声明一个 [`Module`](@ref)，这是一个独立的全局变量工作空间。在模块内，您可以控制从其他模块可见的名称（通过导入），并指定您的名称中哪些是公开的（通过 `export` 和 `public`）。模块允许您创建顶级定义，而无需担心在与其他人的代码一起使用时出现名称冲突。有关更多详细信息，请参见 [关于模块的手册部分](@ref modules)。

# 示例

```julia
module Foo
import Base.show
export MyType, foo

struct MyType
    x
end

bar(x) = 2x
foo(a::MyType) = bar(a.x) + 1
show(io::IO, a::MyType) = print(io, "MyType $(a.x)")
end
```
