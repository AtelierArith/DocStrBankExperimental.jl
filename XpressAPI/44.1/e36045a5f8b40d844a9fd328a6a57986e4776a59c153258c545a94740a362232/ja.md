```
XPRStuneprobsetfile(prob, setfile, ifmip, sense)::prob
```

この関数は、一連の問題に対するチューナーセッションを開始します。

チューナーは、制御設定のリストとそれらの有望な組み合わせを評価しながら、問題を複数回解決します。終了すると、チューナーは問題に最適な制御設定を選択して設定します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `setfile::Union{Nothing,AbstractString}`: 問題ファイル名のリストを含むプレーンテキストファイル。
  * `ifmip::Integer`: -1は問題セットをLPまたはMIPとして自動的に解決するかどうかを判断します; 0はチューナーに問題セットをLPとして調整させることを強制します; 1はチューナーに問題セットをMIPとして調整させることを強制します。
  * `sense::Integer`: 0は各問題のセンスを自動的に判断します; 1はチューナーに各問題を最小化させることを強制します; -1はチューナーに各問題を最大化させることを強制します。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRStuneprobsetfile](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStuneprobsetfile.html)。
