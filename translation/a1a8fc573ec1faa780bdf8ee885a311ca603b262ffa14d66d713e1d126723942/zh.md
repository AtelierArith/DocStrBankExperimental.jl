```
precompile(f, argtypes::Tuple{Vararg{Any}}, m::Method)
```

为给定的参数类型预编译特定的方法。这可以用来预编译与通常通过调度选择的不同的方法，从而模拟 `invoke`。
