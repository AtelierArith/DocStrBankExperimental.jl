```
@nospecialize
```

应用于函数参数名称时，提示编译器该方法实现不应针对该参数的不同类型进行特化，而应使用该参数声明的类型。它可以应用于正式参数列表中的参数，或在函数体内。当应用于参数时，宏必须包裹整个参数表达式，例如 `@nospecialize(x::Real)` 或 `@nospecialize(i::Integer...)`，而不是仅仅包裹参数名称。当在函数体内使用时，宏必须出现在语句位置，并且在任何代码之前。

在没有参数的情况下，它适用于父作用域的所有参数。在局部作用域中，这意味着包含函数的所有参数。在全局（顶层）作用域中，这意味着当前模块中随后定义的所有方法。

通过使用 [`@specialize`](@ref) 可以将特化重置为默认值。

```julia
function example_function(@nospecialize x)
    ...
end

function example_function(x, @nospecialize(y = 1))
    ...
end

function example_function(x, y, z)
    @nospecialize x y
    ...
end

@nospecialize
f(y) = [x for x in y]
@specialize
```

!!! note
    `@nospecialize` 影响代码生成，但不影响推断：它限制了生成的本机代码的多样性，但并不对类型推断施加任何限制（超出标准限制）。使用 [`Base.@nospecializeinfer`](@ref) 结合 `@nospecialize` 以额外抑制推断。


# 示例

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Float64
└──      return %1
) => Float64
```

在这里，`@nospecialize` 注解的结果等同于

```julia
f(A::AbstractArray) = invoke(g, Tuple{AbstractArray}, A)
```

确保只会为 `g` 生成一个版本的本机代码，该版本对任何 `AbstractArray` 都是通用的。然而，`g` 和 `f` 的具体返回类型仍然被推断，并且这仍然用于优化 `f` 和 `g` 的调用者。
