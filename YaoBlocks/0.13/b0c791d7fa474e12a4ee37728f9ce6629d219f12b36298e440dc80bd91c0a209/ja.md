```
print_tree(io, root, node[, depth=1, active_levels=()]; kwargs...)
```

ブロックツリーを印刷します。

# キーワード

  * `maxdepth`: 印刷する最大ツリー深度
  * `charset`: デフォルトは ('├','└','│','─')。`YaoBlocks.BlockTreeCharSet`も参照してください。
  * `title`: タイトルを印刷するかどうかを制御します。`true` または `false`、デフォルトは `true`
