```
XPRSaddcbprenode(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数 `prenode` に渡される問題。
  * `infeasible`: 実現可能性のステータス。ユーザーによって非ゼロの値が設定された場合、現在のノードはオプティマイザによって非実現可能と宣言されます。

`cb` は次のシグネチャで呼び出されます：

```
cb(cbprob)::infeasible
```
