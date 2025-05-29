```
XPRS_bo_getbounds(bo, branch, maxbounds, bndtype, colind, bndval)::nbounds, bndtype, colind, bndval
```

ユーザーブランチオブジェクトのブランチの境界を返します。

# 引数

  * `bo::XPRSbranchobject`: 検査するブランチオブジェクト。
  * `branch::Integer`: 境界を取得するブランチの番号。
  * `maxbounds::Integer`: 返す境界の最大数。
  * `bndtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: 境界のタイプが返される長さ `maxbounds` の文字配列：L下限。 この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。 この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 列インデックスが返される長さ `maxbounds` の整数配列。 この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。 この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `bndval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 境界値が返される長さ `maxbounds` の倍精度配列。 この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。 この引数に `nothing` を渡すことで、その情報を照会しないことができます。

# 戻り値

  * `nbounds::Int32`: 指定されたブランチの境界の数が返される場所。
  * `bndtype::Union{Nothing,AbstractVector{Cchar}}`: 境界のタイプが返される長さ `maxbounds` の文字配列：L下限。
  * `colind::Union{Nothing,AbstractVector{Int32}}`: 列インデックスが返される長さ `maxbounds` の整数配列。
  * `bndval::Union{Nothing,AbstractVector{Float64}}`: 境界値が返される長さ `maxbounds` の倍精度配列。

C APIの対応する関数のドキュメント [XPRS*bo*getbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_getbounds.html) も参照してください。
