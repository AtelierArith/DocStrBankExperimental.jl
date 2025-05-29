```
XPRS_bo_getlasterror(bo, maxbytes)::msgcode, msg, nbytes
```

指定されたブランチオブジェクトに対する呼び出し中に発生した最後のエラーを返します。

# 引数

  * `bo::XPRSbranchobject`: ブランチオブジェクト。
  * `maxbytes::Integer`: 文字バッファ `msg` のサイズ。

# 戻り値

  * `msgcode::Int32`: エラーコードが返される場所。
  * `msg::AbstractString`: 指定されたブランチオブジェクトに関連する最後のエラーメッセージが返されるサイズ `maxbytes` の文字バッファ。
  * `nbytes::Int32`: エラーストリングを完全に返すために必要な文字バッファのサイズ。

C APIの対応する関数 [XPRS*bo*getlasterror](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_getlasterror.html) のドキュメントも参照してください。
