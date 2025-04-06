```
UndefKeywordError(var::Symbol)
```

所需的关键字参数 `var` 在函数调用中未被赋值。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function my_func(;my_arg)
           return my_arg + 1
       end
my_func (generic function with 1 method)

julia> my_func()
ERROR: UndefKeywordError: keyword argument `my_arg` not assigned
Stacktrace:
 [1] my_func() at ./REPL[1]:2
 [2] top-level scope at REPL[2]:1
```
