```
setglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

将模块 `module` 中的绑定 `name` 的值设置或更改为 `x`。不执行类型转换，因此如果绑定已经声明了类型，`x` 必须是适当的类型，否则会抛出错误。

此外，可以为此操作指定原子顺序，否则默认为单调。

用户通常通过 [`setproperty!`](@ref Base.setproperty!) 函数或相应的语法（即 `module.name = x`）访问此功能，因此这仅适用于非常特定的用例。

!!! compat "Julia 1.9"
    此函数需要 Julia 1.9 或更高版本。


另请参见 [`setproperty!`](@ref Base.setproperty!) 和 [`getglobal`](@ref)

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> module M; global a; end;

julia> M.a  # 同 `getglobal(M, :a)`
ERROR: UndefVarError: `a` not defined in `M`
建议：添加适当的导入或赋值。此全局变量已声明但未赋值。
Stacktrace:
 [1] getproperty(x::Module, f::Symbol)
   @ Base ./Base.jl:42
 [2] top-level scope
   @ none:1

julia> setglobal!(M, :a, 1)
1

julia> M.a
1
```
