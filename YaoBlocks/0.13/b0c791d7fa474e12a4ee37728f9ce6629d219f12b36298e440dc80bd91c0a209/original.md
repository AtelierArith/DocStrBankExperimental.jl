```
print_tree(io, root, node[, depth=1, active_levels=()]; kwargs...)
```

Print the block tree.

# Keywords

  * `maxdepth`: max tree depth to print
  * `charset`: default is ('├','└','│','─'). See also `YaoBlocks.BlockTreeCharSet`.
  * `title`: control whether to print the title, `true` or `false`, default is `true`
