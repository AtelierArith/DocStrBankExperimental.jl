```
swapproperty!(x, f::Symbol, v, order::Symbol=:not_atomic)
```

`@atomic a.b, _ = c, a.b` sözdizimi `(c, swapproperty!(a, :b, c, :sequentially_consistent))` döner; burada her iki taraf için ortak bir `getproperty` ifadesi olmalıdır.

Ayrıca bkz. [`swapfield!`](@ref Core.swapfield!) ve [`setproperty!`](@ref Base.setproperty!).
