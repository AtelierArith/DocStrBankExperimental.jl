```
code_typed(f, types; kw...)
```

返回一个类型推断的降级形式（IR）数组，适用于与给定的泛型函数和类型签名匹配的方法。

# 关键字参数

  * `optimize::Bool = true`：可选，控制是否应用额外的优化，例如内联。
  * `debuginfo::Symbol = :default`：可选，控制输出中存在的代码元数据的数量，可能的选项是 `:source` 或 `:none`。

# 内部关键字参数

本节应视为内部，仅供理解Julia编译器内部的人员使用。

  * `world::UInt = Base.get_world_counter()`：可选，控制查找方法时使用的世界年龄，如果未指定，则使用当前世界年龄。
  * `interp::Core.Compiler.AbstractInterpreter = Core.Compiler.NativeInterpreter(world)`：可选，控制要使用的抽象解释器，如果未指定，则使用本地解释器。

# 示例

可以将参数类型放在元组中以获取相应的 `code_typed`。

```julia
julia> code_typed(+, (Float64, Float64))
1-element Vector{Any}:
 CodeInfo(
1 ─ %1 = Base.add_float(x, y)::Float64
└──      return %1
) => Float64
```
