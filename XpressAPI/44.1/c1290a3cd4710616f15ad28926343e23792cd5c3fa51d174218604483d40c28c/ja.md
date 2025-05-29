```
XPRS_bo_addbounds(bo, branch, nbounds, bndtype, colind, bndval)::Nothing
```

ユーザーブランチオブジェクトのブランチに新しい境界を追加します。

# 引数

  * `bo::XPRSbranchobject`: 修正するユーザーブランチオブジェクト。
  * `branch::Integer`: 新しい境界を追加するブランチの番号。
  * `nbounds::Integer`: 追加する新しい境界の数。
  * `bndtype::AbstractVector{Cchar}`: 追加する境界のタイプを示す長さ `nbounds` の文字配列：下限。
  * `colind::AbstractVector{Integer}`: 新しい境界の列インデックスを含む長さ `nbounds` の整数配列。
  * `bndval::AbstractVector{Number}`: 境界値を与える長さ `nbounds` の倍精度配列。

C APIの対応する関数 [XPRS*bo*addbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_addbounds.html) のドキュメントも参照してください。
