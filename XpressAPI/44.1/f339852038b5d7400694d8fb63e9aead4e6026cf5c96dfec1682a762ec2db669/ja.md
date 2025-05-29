```
XPRS_bo_addrows(bo, branch, nrows, ncoefs, rowtype, rhs, start, colind, rowcoef)::Nothing
```

ユーザー分岐オブジェクトのブランチに新しい制約を追加します。

# 引数

  * `bo::XPRSbranchobject`: 修正するユーザー分岐オブジェクト。
  * `branch::Integer`: 新しい制約を追加するブランチの番号。
  * `nrows::Integer`: 追加する新しい制約の数。
  * `ncoefs::Integer`: すべての新しい制約における非ゼロ係数の数。
  * `rowtype::AbstractVector{Cchar}`: 追加する制約のタイプを示す長さ `nrows` の文字配列：LLess thanタイプ。
  * `rhs::AbstractVector{Number}`: 右辺の値を含む長さ `nrows` の倍精度配列。
  * `start::AbstractVector{Integer}`: 新しい制約における非ゼロ係数の開始位置の `colind` および `rowcoef` 配列のオフセットを含む長さ `nrows` の整数配列。
  * `colind::AbstractVector{Integer}`: 非ゼロ係数の列インデックスを含む長さ `ncoefs` の整数配列。
  * `rowcoef::AbstractVector{Number}`: 非ゼロ係数の値を含む長さ `ncoefs` の倍精度配列。

C APIの対応する関数 [XPRS*bo*addrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_addrows.html) のドキュメントも参照してください。
