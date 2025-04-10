```
cumsum(A; dims::Integer)
```

次元 `dims` に沿った累積和。パフォーマンス向上や出力の精度を制御するために、事前に割り当てられた出力配列を使用するには、[`cumsum!`](@ref) も参照してください（例えば、オーバーフローを避けるため）。

# 例

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cumsum(a, dims=1)
2×3 Matrix{Int64}:
 1  2  3
 5  7  9

julia> cumsum(a, dims=2)
2×3 Matrix{Int64}:
 1  3   6
 4  9  15
```

!!! note
    戻り値の配列の `eltype` は、システムワードサイズ未満の符号付き整数の場合は `Int`、システムワードサイズ未満の符号なし整数の場合は `UInt` です。小さな符号付きまたは符号なし整数の配列の `eltype` を保持するには、`accumulate(+, A)` を使用する必要があります。

    ```jldoctest
    julia> cumsum(Int8[100, 28])
    2-element Vector{Int64}:
     100
     128

    julia> accumulate(+,Int8[100, 28])
    2-element Vector{Int8}:
      100
     -128
    ```

    前者の場合、整数はシステムワードサイズに拡張され、その結果は `Int64[100, 128]` になります。後者の場合、そのような拡張は行われず、整数のオーバーフローが `Int8[100, -128]` になります。

