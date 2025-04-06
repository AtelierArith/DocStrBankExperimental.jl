```
Meta.show_sexpr([io::IO,], ex)
```

以 lisp 风格的 S 表达式显示表达式 `ex`。

# 示例

```jldoctest
julia> Meta.show_sexpr(:(f(x, g(y,z))))
(:call, :f, :x, (:call, :g, :y, :z))
```
