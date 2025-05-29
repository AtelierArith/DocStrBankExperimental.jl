直交座標系、`Coords`のサブタイプ。

座標の列を持つ`Array{Float64, 2}`を渡すことで構築します。

例えば、

```julia
c_coords = Cart(rand(3, 2))  # 2つの粒子
c_coords.x                   # 直交座標を取得
```
