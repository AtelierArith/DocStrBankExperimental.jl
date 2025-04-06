```
StackFrame
```

スタック情報は実行コンテキストを表し、以下のフィールドを持ちます：

  * `func::Symbol`

    実行コンテキストを含む関数の名前。
  * `linfo::Union{Core.MethodInstance, Method, Module, Core.CodeInfo, Nothing}`

    実行コンテキストを含むMethodInstanceまたはCodeInfo（見つかった場合）、またはモジュール（マクロ展開用）
  * `file::Symbol`

    実行コンテキストを含むファイルへのパス。
  * `line::Int`

    実行コンテキストを含むファイル内の行番号。
  * `from_c::Bool`

    コードがCからのものであれば真。
  * `inlined::Bool`

    コードがインラインフレームからのものであれば真。
  * `pointer::UInt64`

    `backtrace`によって返される実行コンテキストへのポインタの表現。
