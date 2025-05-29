```
zopen(s::AbstractStore, mode="r"; consolidated = false, path = "", lru = 0)
```

Opens a zarr Array or Group at Store `s`. If `consolidated` is set to "true", Zarr will search for a consolidated metadata field as created by the python zarr `consolidate_metadata` function. This can substantially speed up metadata parsing of large zarr groups. Setting `lru` to a value > 0 means that chunks that have been accessed before will be cached and consecutive reads will happen from the cache.  Here, `lru` denotes the number of chunks that remain in memory. 
