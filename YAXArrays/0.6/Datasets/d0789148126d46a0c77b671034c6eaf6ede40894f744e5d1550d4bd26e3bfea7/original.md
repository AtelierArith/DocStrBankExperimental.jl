```
setchunks(c::Dataset,chunks)
```

Resets the chunks of all or a subset YAXArrays in the dataset and returns a new Dataset. Note that this will not change the chunking of the underlying data itself, it will just make the data "look" like it had a different chunking. If you need a persistent on-disk representation of this chunking, use `savedataset` on the resulting array. The `chunks` argument can take one of the following forms:

  * a NamedTuple or AbstractDict mapping from variable name to a description of the desired variable chunks
  * a NamedTuple or AbstractDict mapping from dimension name to a description of the desired variable chunks
  * a description of the desired variable chunks applied to all members of the Dataset

where a description of the desired variable chunks can take one of the following forms:

  * a `DiskArrays.GridChunks` object
  * a tuple specifying the chunk size along each dimension
  * an AbstractDict or NamedTuple mapping one or more axis names to chunk sizes
