```
return
```

`return x` 使得封闭的函数提前退出，将给定的值 `x` 返回给调用者。单独使用 `return` 而不带值等同于 `return nothing`（参见 [`nothing`](@ref)）。

```julia
function compare(a, b)
    a == b && return "equal to"
    a < b ? "less than" : "greater than"
end
```

一般来说，你可以在函数体内的任何位置放置 `return` 语句，包括深度嵌套的循环或条件中，但要小心 `do` 块。例如：

```julia
function test1(xs)
    for x in xs
        iseven(x) && return 2x
    end
end

function test2(xs)
    map(xs) do x
        iseven(x) && return 2x
        x
    end
end
```

在第一个例子中，返回在遇到偶数时立即退出 `test1`，因此 `test1([5,6,7])` 返回 `12`。

你可能期望第二个例子的行为相同，但实际上那里的 `return` 仅仅是退出 *内部* 函数（在 `do` 块内），并将值返回给 `map`。因此 `test2([5,6,7])` 返回 `[5,12,7]`。

当在顶层表达式中使用时（即在任何函数外部），`return` 会导致整个当前的顶层表达式提前终止。
