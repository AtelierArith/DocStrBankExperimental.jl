```
XPRSgetcutlist(prob, cuttype, interp, maxcuts, cutind)::ncuts, cutind
```

現在のノードでアクティブなカットのポインタのリストを取得します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `cuttype::Integer`: 返されるカットのユーザー定義タイプ。
  * `interp::Integer`: カットタイプの解釈方法: -1はすべてのカットを取得; 1はカットタイプを数値として扱う; 2はカットタイプをビットマップとして扱う - `cuttype`に設定されたビットのいずれかが一致する場合にカットを取得; 3はカットタイプをビットマップとして扱う - `cuttype`に設定されたすべてのビットが一致する場合にカットを取得。
  * `maxcuts::Integer`: 取得するカットの最大数。
  * `cutind::Union{XPRSallocatable,AbstractVector{Ptr{Cvoid}}}`: カットのポインタが返される長さ`maxcuts`の配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てることができます。

# 戻り値

  * `ncuts::Int32`: アクティブなカットの数が返される整数へのポインタ。
  * `cutind::AbstractVector{Ptr{Cvoid}}`: カットのポインタが返される長さ`maxcuts`の配列。

C APIの対応する関数[XPRSgetcutlist](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcutlist.html)のドキュメントも参照してください。
