```
Experimental.register_error_hint(handler, exceptiontype)
```

注册一个“提示”函数 `handler(io, exception)`，该函数可以建议用户绕过错误的潜在方法。`handler` 应该检查 `exception` 以确定是否满足提示的条件，如果满足，则生成输出到 `io`。包应该在其 `__init__` 函数中调用 `register_error_hint`。

对于特定的异常类型，`handler` 需要接受额外的参数：

  * `MethodError`：提供 `handler(io, exc::MethodError, argtypes, kwargs)`，它将组合的参数拆分为位置参数和关键字参数。

发出提示时，输出通常应以 `\n` 开头。

如果您定义了自定义异常类型，您的 `showerror` 方法可以通过调用 [`Experimental.show_error_hints`](@ref) 来支持提示。

# 示例

```
julia> module Hinter

       only_int(x::Int)      = 1
       any_number(x::Number) = 2

       function __init__()
           Base.Experimental.register_error_hint(MethodError) do io, exc, argtypes, kwargs
               if exc.f == only_int
                    # 颜色不是必需的，这只是为了显示这是可能的。
                    print(io, "\n您是想调用 ")
                    printstyled(io, "`any_number`?", color=:cyan)
               end
           end
       end

       end
```

然后，如果您在不是 `Int` 的东西上调用 `Hinter.only_int`（从而触发 `MethodError`），它会发出提示：

```
julia> Hinter.only_int(1.0)
ERROR: MethodError: no method matching only_int(::Float64)
函数 `only_int` 存在，但没有为此参数类型组合定义方法。
您是想调用 `any_number`?
最近的候选者是：
    ...
```

!!! compat "Julia 1.5"
    自定义错误提示自 Julia 1.5 起可用。


!!! warning
    此接口是实验性的，可能会在没有通知的情况下更改或删除。为了保护自己免受更改的影响，请考虑将任何注册放在 `if isdefined(Base.Experimental, :register_error_hint) ... end` 块中。

