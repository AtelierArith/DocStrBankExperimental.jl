```
ディスパッチ
```

アクターはその `Dispatch` モードに応じて、動作関数への引数を構成します：

  * `full`: [`Become`](@ref) `args...` と `msg.x...` から。これがデフォルトのディスパッチモードです。
  * `state`: アクターの状態と `msg.x...` から。この場合、アクターは動作関数の結果で状態を更新します。結果は `Tuple` に保存されます。
