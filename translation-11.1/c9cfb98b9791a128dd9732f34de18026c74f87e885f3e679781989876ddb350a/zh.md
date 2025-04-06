```
@noinline
```

给编译器一个提示，表明它不应该内联一个函数。

小函数通常会自动被内联。通过在小函数上使用 `@noinline`，可以防止自动内联。

`@noinline` 可以在函数定义之前或在函数体内使用。

```julia
# 注释长形式定义
@noinline function longdef(x)
    ...
end

# 注释短形式定义
@noinline shortdef(x) = ...

# 注释一个 `do` 块创建的匿名函数
f() do
    @noinline
    ...
end
```

!!! compat "Julia 1.8"
    在函数体内的使用需要至少 Julia 1.8。


---

```
@noinline block
```

给编译器一个提示，表明它不应该内联 `block` 内的调用。

```julia
# 编译器将尝试不内联 `f`
@noinline f(...)

# 编译器将尝试不内联 `f`、`g` 和 `+`
@noinline f(...) + g(...)
```

!!! note
    调用位置注释总是优先于应用于被调用函数定义的注释：

    ```julia
    @inline function explicit_inline(args...)
        # body
    end

    let
        @noinline explicit_inline(args...) # 将不会被内联
    end
    ```


!!! note
    当存在嵌套的调用位置注释时，最内层的注释具有优先权：

    ```julia
    @inline let a0, b0 = ...
        a = @noinline f(a0)  # 编译器将不会尝试内联此调用
        b = f(b0)            # 编译器将尝试内联此调用
        return a, b
    end
    ```


!!! compat "Julia 1.8"
    调用位置注释需要至少 Julia 1.8。


---

!!! note
    如果函数是微不足道的（例如返回一个常量），它可能仍然会被内联。

