```
align(src::String, tgt::String; costmodel::BioAlignments.CostModel=BioAlignments.CostModel(match=0, mismatch=1, insertion=1, deletion=1))
```

`tgt` 文字列を `src` 文字列に特定の `costmodel` を使用して整列させます。
