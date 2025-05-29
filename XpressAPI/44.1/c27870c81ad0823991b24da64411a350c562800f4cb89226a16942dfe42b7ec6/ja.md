```
XPRSdelpwlcons(prob, npwls, pwlind)::prob
```

問題から区分線形制約を削除します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `npwls::Integer`: 削除する区分線形制約の数。
  * `pwlind::AbstractVector{Integer}`: 削除する区分線形制約を含む長さ `npwls` の整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSdelpwlcons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelpwlcons.html) のドキュメントも参照してください。
