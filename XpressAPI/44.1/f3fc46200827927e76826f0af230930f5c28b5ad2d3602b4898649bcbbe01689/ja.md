```
XPRSmsaddjob(prob, description, ninitial, colind, initial, nintcontrols, intcontrolid, intcontrolval, ndblcontrols, dblcontrolid, dblcontrolval, data)::prob
```

マルチスタートジョブをマルチスタートプールに追加します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `description::Union{Nothing,AbstractString}`: ジョブのテキスト説明。
  * `ninitial::Integer`: 設定する初期値の数。
  * `colind::AbstractVector{Integer}`: 初期値を設定する変数のインデックス。
  * `initial::AbstractVector{Number}`: 初期値を設定する変数の初期値。
  * `nintcontrols::Integer`: 設定する整数制御の数。
  * `intcontrolid::AbstractVector{Integer}`: 設定される整数制御のインデックス。
  * `intcontrolval::AbstractVector{Integer}`: 設定される整数制御の値。
  * `ndblcontrols::Integer`: 設定する倍精度制御の数。
  * `dblcontrolid::AbstractVector{Integer}`: 設定される倍精度制御のインデックス。
  * `dblcontrolval::AbstractVector{Number}`: 設定される倍精度制御の値。
  * `data::Any`: マルチスタートコールバックに渡されるジョブ固有のユーザーコンテキストポインタ。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSmsaddjob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmsaddjob.html)のドキュメントも参照してください。
