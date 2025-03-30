```
modifyproperty!(x, f::Symbol, op, v, order::Symbol=:not_atomic)
```

语法 `@atomic op(x.f, v)`（及其等效形式 `@atomic x.f op v`）返回 `modifyproperty!(x, :f, op, v, :sequentially_consistent)`，其中第一个参数必须是 `getproperty` 表达式，并且是以原子方式修改的。

调用 `op(getproperty(x, f), v)` 必须返回一个可以默认存储在对象 `x` 的字段 `f` 中的值。特别地，与 [`setproperty!`](@ref Base.setproperty!) 的默认行为不同，`convert` 函数不会被自动调用。

另请参见 [`modifyfield!`](@ref Core.modifyfield!) 和 [`setproperty!`](@ref Base.setproperty!)。
