空間内の原子のセットを表すために使用されます（その原子種と座標）。

```julia
struct Atoms{T <: Coords} # 指定された型が `Coords` であることを強制
    n::Int # 原子の数は？
    species::Array{Symbol, 1} # 種類のリスト
    coords::T # 座標
end
```

ここで、`T` は `Frac` または `Cart` です。

ヘルパーコンストラクタ（`n` を推論します）：

```julia
species = [:H, :H]
coords = Cart(rand(3, 2))
atoms = Atoms(species, coords)
```
