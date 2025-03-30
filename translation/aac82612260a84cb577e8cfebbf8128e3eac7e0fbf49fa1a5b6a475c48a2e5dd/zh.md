```
__init__
```

`__init__()` 函数在模块首次运行时加载后立即执行。它在模块中所有其他语句执行完毕后被调用一次。由于它是在完全导入模块后被调用的，因此子模块的 `__init__` 函数会首先执行。`__init__` 的两个典型用途是调用外部 C 库的运行时初始化函数和初始化涉及外部库返回的指针的全局常量。有关更多详细信息，请参见 [manual section about modules](@ref modules)。

# 示例

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```
