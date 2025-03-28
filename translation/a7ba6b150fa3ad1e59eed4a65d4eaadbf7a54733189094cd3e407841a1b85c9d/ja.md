```
x && y
```

ショートサーキットブールAND。

関連情報としては、[`&`](@ref)、三項演算子 `? :`、および[制御フロー](@ref man-conditional-evaluation)に関するマニュアルのセクションを参照してください。

# 例

```jldoctest
julia> x = 3;

julia> x > 1 && x < 10 && x isa Int
true

julia> x < 0 && error("expected positive x")
false
```
