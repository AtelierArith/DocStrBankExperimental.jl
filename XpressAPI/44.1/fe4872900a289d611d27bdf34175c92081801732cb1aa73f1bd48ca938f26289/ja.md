```
XPRSloadpresolvedirs(prob, ndirs, colind, priority, dir, uppseudo, downpseudo)::prob
```

指示を事前解決行列に読み込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ndirs::Integer`: 指示の数。
  * `colind::AbstractVector{Integer}`: 列番号を含む長さ `ndirs` の整数配列。
  * `priority::AbstractVector{Integer}`: 列またはセットの優先順位を含む長さ `ndirs` の整数配列。
  * `dir::AbstractVector{Cchar}`: 各列またはセットの分岐方向を指定する長さ `ndirs` の文字配列：Uエンティティを上に強制する; Dエンティティを下に強制する; N指定なし。必要ない場合は `nothing` である可能性があります。
  * `uppseudo::AbstractVector{Number}`: 列またはセットの上の擬似コストを含む長さ `ndirs` の倍精度配列。
  * `downpseudo::AbstractVector{Number}`: 列またはセットの下の擬似コストを含む長さ `ndirs` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSloadpresolvedirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadpresolvedirs.html) のドキュメントも参照してください。
