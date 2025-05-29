```
align(src::Array{String}, tgt::Array{String}; 
	costmodel::CostModel=CostModel(match=0, mismatch=1, insertion=1, deletion=0),
	store_results::Bool=true
)
```

ALign `tgt` array of texts to `src` array of texts using a particular `costmodel` from BioAlignments.jl. `store_results` if results of alignment are stored or returned,  otherwise, only the scores are returned.
