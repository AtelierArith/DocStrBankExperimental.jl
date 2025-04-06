```
@macroexpand [mod,] ex
```

返回等效的表达式，所有宏已被移除（展开）。如果提供了两个参数，第一个是要在其中评估的模块。

`@macroexpand` 和 [`macroexpand`](@ref) 之间存在差异。

  * 虽然 [`macroexpand`](@ref) 接受一个关键字参数 `recursive`，`@macroexpand` 始终是递归的。有关非递归宏版本，请参见 [`@macroexpand1`](@ref)。
  * 虽然 [`macroexpand`](@ref) 有一个显式的 `module` 参数，`@macroexpand` 始终相对于调用它的模块进行展开。

这在以下示例中最好理解：

```julia-repl
julia> module M
           macro m()
               1
           end
           function f()
               (@macroexpand(@m),
                macroexpand(M, :(@m)),
                macroexpand(Main, :(@m))
               )
           end
       end
M

julia> macro m()
           2
       end
@m (macro with 1 method)

julia> M.f()
(1, 1, 2)
```

使用 `@macroexpand` 时，表达式在代码中 `@macroexpand` 出现的地方展开（示例中的模块 `M`）。使用 `macroexpand` 时，表达式在作为第一个参数给定的模块中展开。

!!! compat "Julia 1.11"
    两个参数的形式至少需要 Julia 1.11。

