空間内の部分点電荷のセットを表すために使用されます（それらの電荷と座標）。

```julia
struct Charges{T <: Coords} # 指定された型が `Coords` であることを強制
    n::Int
    q::Array{Float64, 1}
    coords::T
end
```

ここで、`T` は `Frac` または `Cart` です。

ヘルパーコンストラクタ（`n` を推論します）：

```julia
q = [0.1, -0.1]
coords = Cart(rand(3, 2))
charges = Charges(q, coords)
```
