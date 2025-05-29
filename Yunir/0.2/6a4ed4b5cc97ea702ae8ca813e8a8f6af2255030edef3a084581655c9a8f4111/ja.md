```
align(src::Array{String}, tgt::Array{String}; 
	costmodel::CostModel=CostModel(match=0, mismatch=1, insertion=1, deletion=0),
	store_results::Bool=true
)
```

`src` テキストの配列に `tgt` テキストの配列を特定の `costmodel` を使用してアラインします。`store_results` はアラインメントの結果が保存されるか返されるかを示し、そうでない場合はスコアのみが返されます。
