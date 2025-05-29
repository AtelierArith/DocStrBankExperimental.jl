```
XPRSgetprimalray(prob, ray)::ray, hasray
```

現在の問題に対してプライマルレイ（プライマル無限方向）を取得します。問題が無限大であると判断された場合に限ります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ray::Union{XPRSallocatable,AbstractVector{Float64}}`: レイを保持するための長さCOLSのダブル配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。

# 戻り値

  * `ray::AbstractVector{Float64}`: レイを保持するための長さCOLSのダブル配列。
  * `hasray::Int32`: 最適化ツールがプライマルレイを返すことができる場合は1に設定され、それ以外の場合は0に設定されます。

C APIの対応する関数[XPRSgetprimalray](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetprimalray.html)のドキュメントも参照してください。
