```
UndefVarError(var::Symbol, [scope])
```

当前作用域中的符号未定义。

# 示例

```jldoctest
julia> a
ERROR: UndefVarError: `a` not defined in `Main`

julia> a = 1;

julia> a
1
```
