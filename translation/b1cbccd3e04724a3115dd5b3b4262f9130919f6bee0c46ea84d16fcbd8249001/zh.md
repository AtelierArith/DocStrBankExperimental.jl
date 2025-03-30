```
getglobal(module::Module, name::Symbol, [order::Symbol=:monotonic])
```

从模块 `module` 中检索绑定 `name` 的值。可以选择为操作定义原子顺序，否则默认为单调。

虽然使用 [`getfield`](@ref) 访问模块绑定仍然被支持以保持兼容性，但应始终优先使用 `getglobal`，因为 `getglobal` 允许控制原子顺序（`getfield` 始终是单调的），并更好地向用户和编译器表明代码的意图。

大多数用户不应直接调用此函数 – 除少数非常特定的用例外，应优先使用 [`getproperty`](@ref Base.getproperty) 函数或相应的语法（即 `module.name`）。

!!! compat "Julia 1.9"
    此函数需要 Julia 1.9 或更高版本。


另请参见 [`getproperty`](@ref Base.getproperty) 和 [`setglobal!`](@ref)。

# 示例

```jldoctest
julia> a = 1
1

julia> module M
       a = 2
       end;

julia> getglobal(@__MODULE__, :a)
1

julia> getglobal(M, :a)
2
```
