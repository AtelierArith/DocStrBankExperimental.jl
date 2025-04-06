```
finalizer(f, x)
```

注册一个函数 `f(x)`，当没有程序可访问的对 `x` 的引用时调用，并返回 `x`。`x` 的类型必须是 `mutable struct`，否则该函数将抛出异常。

`f` 不能导致任务切换，这排除了大多数 I/O 操作，例如 `println`。使用 `@async` 宏（将上下文切换推迟到最终器外部）或 `ccall` 直接调用 C 中的 I/O 函数可能对调试有帮助。

请注意，执行 `f` 时没有保证的世界年龄。它可能在注册最终器的世界年龄或任何后来的世界年龄中被调用。

# 示例

```julia
finalizer(my_mutable_struct) do x
    @async println("Finalizing $x.")
end

finalizer(my_mutable_struct) do x
    ccall(:jl_safe_printf, Cvoid, (Cstring, Cstring), "Finalizing %s.", repr(x))
end
```

可以在对象构造时注册最终器。在以下示例中，请注意我们隐式依赖于最终器返回新创建的可变结构体 `x`。

```julia
mutable struct MyMutableStruct
    bar
    function MyMutableStruct(bar)
        x = new(bar)
        f(t) = @async println("Finalizing $t.")
        finalizer(f, x)
    end
end
```
