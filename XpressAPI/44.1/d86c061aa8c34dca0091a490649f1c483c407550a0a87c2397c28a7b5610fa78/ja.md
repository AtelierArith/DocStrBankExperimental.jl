```
XPRSsetindicators(prob, nrows, rowind, colind, complement)::prob
```

ツリー探索中に行列の行のセットをインジケーター制約として扱うことを指定します。

インジケーター制約は、`condition`と`constraint`で構成されます。`condition`は"`bin = value`"の形式で、`bin`はバイナリ変数であり、`value`は0または1のいずれかです。`constraint`は任意の行列の行（線形、二次、または一般的な非線形である可能性があります）です。ツリー探索中に、インジケーター制約として構成された行は、条件が成立する場合、つまりインジケーター変数`bin`が指定された値を持つ場合にのみ強制されます。すべての行には、単一のインジケーター変数と項のみが割り当てられることに注意してください。行が複数の異なる項によってアクティブにする必要がある場合、その行は複製され、各項が異なる行に割り当てられる必要があります。インジケーター変数を変更する必要がある場合、古い項は最初に削除する必要があります（XPRSdelindicatorsを呼び出すか、comps引数を0にしてこの関数を呼び出すことによって）新しい項を割り当てる前に。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: インジケーター制約の数。
  * `rowind::AbstractVector{Integer}`: インジケーター制約の制約部分を定義する行のインデックスを含む長さ`nrows`の整数配列。
  * `colind::AbstractVector{Integer}`: インジケーター変数の列インデックスを含む長さ`nrows`の整数配列。
  * `complement::AbstractVector{Integer}`: 補完フラグを持つ長さ`nrows`の整数配列：0はインジケーター制約ではない（この場合、`colind`配列の対応するエントリは無視されます）；1は"`bin = 1`"の条件を持つインジケーター制約；-1は"`bin = 0`"の条件を持つインジケーター制約。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetindicators](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetindicators.html)のドキュメントも参照してください。
