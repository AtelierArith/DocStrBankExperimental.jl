```
抽象类型
```

`抽象类型` 声明一个不能被实例化的类型，仅作为类型图中的一个节点，从而描述一组相关的具体类型：那些具体类型是它们的子类。抽象类型形成了概念层次结构，使得 Julia 的类型系统不仅仅是对象实现的集合。例如：

```julia
abstract type Number end
abstract type Real <: Number end
```

[`Number`](@ref) 没有超类型，而 [`Real`](@ref) 是 `Number` 的一个抽象子类型。
