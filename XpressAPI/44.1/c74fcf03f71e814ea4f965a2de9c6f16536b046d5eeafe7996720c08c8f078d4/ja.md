```
XPRSgetdualray(prob, ray)::ray, hasray
```

現在の問題に対して双対レイ（双対無限方向）を取得します。問題が非可行であると判断された場合に限ります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ray::Union{XPRSallocatable,AbstractVector{Float64}}`: レイを保持するための長さROWSの倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。

# 戻り値

  * `ray::AbstractVector{Float64}`: レイを保持するための長さROWSの倍精度配列。
  * `hasray::Int32`: 最適化ツールが双対レイを返すことができる場合は1に、そうでない場合は0に設定される変数です。

C APIの対応する関数のドキュメントも参照してください [XPRSgetdualray](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetdualray.html)。
