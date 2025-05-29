```
XPRSrepairinfeas(prob, penalty, phase2, flags, lepref, gepref, lbpref, ubpref, delta)::status
```

XPRSrepairweightedinfeasの簡略化されたインターフェースを提供します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `penalty::Integer`: 優先順位から作成されるペナルティのタイプ：各ペナルティは優先順位の逆数です（デフォルト）；ペナルティはスケーリングされた問題に配置されます。
  * `phase2::Integer`: 最適化の第2フェーズを制御します：元の問題の目的感を使用します（デフォルト）；元の目的を使用して緩和された問題を最大化します；元の目的に関して最適化をスキップします；元の目的を使用して緩和された問題を最小化します；緩和が非可行である場合、問題の分析のために縮小不可能な非可行部分集合を生成します；緩和が非可行である場合、問題の分析のためにすべての縮小不可能な非可行部分集合を生成します。
  * `flags::Integer`: どのタイプの解決を行うべきかを指定します：MIPとしてgsolve（デフォルト）；変数の離散性を無視した線形モデルとしてlsolve；グローバルソルバーをxcallします。
  * `lepref::Float64`: 行の小さいまたは等しい側を緩和するための優先順位。
  * `gepref::Float64`: 行の大きいまたは等しい側を緩和するための優先順位。
  * `lbpref::Float64`: 下限を緩和するための優先順位。
  * `ubpref::Float64`: 上限を緩和するための優先順位。
  * `delta::Float64`: 第2フェーズにおける緩和の乗数 -1。

# 戻り値

  * `status::Int32`: 緩和後のステータス：0緩和された最適解が見つかりました；1緩和された問題は非可行です；2緩和された問題は無限大です；3元の目的に関して緩和された問題の解は最適ではありません；4エラー（戻りコードがゼロでない場合）；5数値的不安定性；6非可行な緩和の分析が行われましたが、緩和は可行です。

C APIの対応する関数[XPRSrepairinfeas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrepairinfeas.html)のドキュメントも参照してください。
