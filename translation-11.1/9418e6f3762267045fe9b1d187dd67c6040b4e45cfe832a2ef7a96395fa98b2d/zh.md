```
replacefield!(value, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
replacefield!(value, i::Int, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

原子性地执行操作以获取并有条件地将字段设置为给定值。

```
y = getfield(value, name, fail_order)
ok = y === expected
if ok
    setfield!(value, name, desired, success_order)
end
return (; old = y, success = ok)
```

如果硬件支持，这可能会优化为适当的硬件指令，否则将使用循环。

!!! compat "Julia 1.7"
    此函数需要 Julia 1.7 或更高版本。

