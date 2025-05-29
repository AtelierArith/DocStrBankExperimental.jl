```
align(src::String, tgt::String; costmodel::BioAlignments.CostModel=BioAlignments.CostModel(match=0, mismatch=1, insertion=1, deletion=1))
```

Align `tgt` string to `src` string using a particular `costmodel` from BioAlignments.jl.
