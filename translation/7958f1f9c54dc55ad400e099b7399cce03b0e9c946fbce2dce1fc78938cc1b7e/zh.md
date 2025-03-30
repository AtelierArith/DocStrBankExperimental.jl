```
ℯ
e
```

常数 ℯ。

Unicode `ℯ` 可以通过在 Julia REPL 中输入 `\euler` 并按下 tab 键来输入，在许多编辑器中也是如此。

另请参见: [`exp`](@ref), [`cis`](@ref), [`cispi`](@ref)。

# 示例

```jldoctest
julia> ℯ
ℯ = 2.7182818284590...

julia> log(ℯ)
1

julia> ℯ^(im)π ≈ -1
true
```
