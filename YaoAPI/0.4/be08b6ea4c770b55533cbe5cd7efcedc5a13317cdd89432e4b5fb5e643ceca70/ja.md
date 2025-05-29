```
collapseto!(register, config)
```

`register`をビット文字列リテラル`bit_str`（または同等の整数）に設定します。ビット文字列リテラルについては、[`@bit_str`](@ref)を参照してください。このインターフェースはエミュレーション専用です。

### 例

以下のコードは、ランダムな状態を特定の状態に崩壊させます。

```jldoctest; setup=:(using Yao)
julia> measure(collapseto!(rand_state(3), bit"001"); nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 001 ₍₂₎
 001 ₍₂₎
 001 ₍₂₎
```
