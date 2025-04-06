```
Base.@constprop 设置 [ex]
```

控制注释函数的跨过程常量传播模式。

支持两种 `setting`：

  * `Base.@constprop :aggressive [ex]`：积极地应用常量传播。对于返回类型依赖于参数值的方法，这可以在增加编译时间的代价下产生更好的推断结果。
  * `Base.@constprop :none [ex]`：禁用常量传播。这可以减少 Julia 可能认为值得进行常量传播的函数的编译时间。常见情况是对于具有 `Bool` 或 `Symbol` 值参数或关键字参数的函数。

`Base.@constprop` 可以在函数定义之前立即应用，或在函数体内应用。

```julia
# 注释长形式定义
Base.@constprop :aggressive function longdef(x)
    ...
end

# 注释短形式定义
Base.@constprop :aggressive shortdef(x) = ...

# 注释 `do` 块创建的匿名函数
f() do
    Base.@constprop :aggressive
    ...
end
```

!!! compat "Julia 1.10"
    在函数体内的使用需要至少 Julia 1.10。

