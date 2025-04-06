```
macroexpand(m::Module, x; recursive=true)
```

取表达式 `x`，并返回一个等效的表达式，去除所有宏（展开），以便在模块 `m` 中执行。`recursive` 关键字控制是否也展开更深层次的嵌套宏。下面的示例演示了这一点：

```julia-repl
julia> module M
           macro m1()
               42
           end
           macro m2()
               :(@m1())
           end
       end
M

julia> macroexpand(M, :(@m2()), recursive=true)
42

julia> macroexpand(M, :(@m2()), recursive=false)
:(#= REPL[16]:6 =# M.@m1)
```
