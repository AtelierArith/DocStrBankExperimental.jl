```
applicable(f, args...) -> Bool
```

与えられた汎用関数が与えられた引数に適用可能なメソッドを持っているかどうかを判断します。

参照: [`hasmethod`](@ref).

# 例

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```
