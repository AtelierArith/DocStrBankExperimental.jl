```
gradient(() -> loss(), ps::Params) -> Grads
```

暗黙のパラメータを持つ勾配。引数のない関数を取り、キーが配列 `x in ps` である辞書のようなコンテナを返します。

`loss()` の値を保持するには、[`withgradient`](@ref) を参照してください。

```jldoctest; setup=:(using Zygote)
julia> x = [1 2 3; 4 5 6]; y = [7, 8]; z = [1, 10, 100];

julia> g = gradient(Params([x, y])) do
         sum(x .* y .* z')
       end
Grads(...)

julia> g[x]
2×3 Matrix{Float64}:
 7.0  70.0  700.0
 8.0  80.0  800.0

julia> haskey(g, z)  # x と y のみがパラメータ
false
```
