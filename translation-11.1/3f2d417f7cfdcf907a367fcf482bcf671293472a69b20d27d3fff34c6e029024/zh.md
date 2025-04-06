```
struct
```

在Julia中最常用的类型是结构体，指定为一个名称和一组字段。

```julia
struct Point
    x
    y
end
```

字段可以有类型限制，这些限制可以是参数化的：

```julia
struct Point{X}
    x::X
    y::Float64
end
```

结构体还可以通过`<:`语法声明一个抽象超类型：

```julia
struct Point <: AbstractPoint
    x
    y
end
```

`struct`默认是不可变的；这些类型的实例在构造后不能被修改。请使用[`mutable struct`](@ref)来声明一个可以修改其实例的类型。

有关更多详细信息，例如如何定义构造函数，请参见手册中的[复合类型](@ref)部分。
