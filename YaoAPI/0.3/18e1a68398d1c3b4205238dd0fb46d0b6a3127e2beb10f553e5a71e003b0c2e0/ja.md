```
focus(f, register, locs...)
```

呼び出し可能な `f` を `focus` のコンテキストで呼び出します。詳細は [`focus!`](@ref) を参照してください。

# 例

フォーカスされたレジスタを印刷します

```julia
julia> r = ArrayReg(bit"101100")
ArrayReg{1,Complex{Float64},Array...}
    active qudits: 6/6

julia> focus(x->(println(x);x), r, 1, 2);
ArrayReg{1,Complex{Float64},Array...}
    active qudits: 2/6
```
