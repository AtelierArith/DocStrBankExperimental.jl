```
XPRSsparsebtran(prob, val, ind)::val, ind, ncoefs
```

ユーザーが提供した（行）ベクトルを現在の行列の逆行列で後ろに掛け算します。

XPRSbtranのスパースバージョンです。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `val::AbstractVector{Float64}`: 基底の逆行列で後ろに掛け算される値を含む長さROWSのダブル配列。
  * `ind::AbstractVector{Int32}`: `val`の非ゼロエントリを特定する整数配列。

# 戻り値

  * `val::AbstractVector{Float64}`: 基底の逆行列で後ろに掛け算される値を含む長さROWSのダブル配列。
  * `ind::AbstractVector{Int32}`: `val`の非ゼロエントリを特定する整数配列。
  * `ncoefs::Int32`: 非ゼロエントリの数が与えられるメモリ位置。

C APIの対応する関数[XPRSsparsebtran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsparsebtran.html)のドキュメントも参照してください。
