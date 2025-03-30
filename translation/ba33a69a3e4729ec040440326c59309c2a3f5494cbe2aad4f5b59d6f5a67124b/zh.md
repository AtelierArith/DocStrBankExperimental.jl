```
@inline
```

给编译器一个提示，表明这个函数值得进行内联。

小函数通常不需要 `@inline` 注解，因为编译器会自动处理。通过在较大的函数上使用 `@inline`，可以给编译器一个额外的推动力来进行内联。

`@inline` 可以在函数定义之前或函数体内立即应用。

```julia
# 注解长形式定义
@inline function longdef(x)
    ...
end

# 注解短形式定义
@inline shortdef(x) = ...

# 注解 `do` 块创建的匿名函数
f() do
    @inline
    ...
end
```

!!! compat "Julia 1.8"
    在函数体内的使用至少需要 Julia 1.8。


---

```
@inline block
```

给编译器一个提示，表明 `block` 内的调用值得进行内联。

```julia
# 编译器将尝试内联 `f`
@inline f(...)

# 编译器将尝试内联 `f`、`g` 和 `+`
@inline f(...) + g(...)
```

!!! note
    调用点注解总是优先于应用于被调用函数定义的注解：

    ```julia
    @noinline function explicit_noinline(args...)
        # body
    end

    let
        @inline explicit_noinline(args...) # 将被内联
    end
    ```


!!! note
    当存在嵌套的调用点注解时，最内层的注解具有优先权：

    ```julia
    @noinline let a0, b0 = ...
        a = @inline f(a0)  # 编译器将尝试内联此调用
        b = f(b0)          # 编译器将不会尝试内联此调用
        return a, b
    end
    ```


!!! warning
    尽管调用点注解将尝试强制内联，无论成本模型如何，但仍然有可能无法成功。特别是，递归调用即使被注解为 `@inline` 也无法进行内联。


!!! compat "Julia 1.8"
    调用点注解至少需要 Julia 1.8。

