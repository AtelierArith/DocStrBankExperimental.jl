```
setchunks(c::YAXArray,chunks)
```

Resets the chunks of a YAXArray and returns a new YAXArray. Note that this will not change the chunking of the underlying data itself,  it will just make the data "look" like it had a different chunking. If you need a persistent on-disk representation of this chunking, use `savecube` on the resulting array. The `chunks` argument can take one of the following forms:

  * a `DiskArrays.GridChunks` object
  * a tuple specifying the chunk size along each dimension
  * an AbstractDict or NamedTuple mapping one or more axis names to chunk sizes
