zcreate(T, dims...;kwargs)

Creates a new empty zarr array with element type `T` and array dimensions `dims`. The following keyword arguments are accepted:

  * `path=""` directory name to store a persistent array. If left empty, an in-memory array will be created
  * `name=""` name of the zarr array, defaults to the directory name
  * `storagetype` determines the storage to use, current options are `DirectoryStore` or `DictStore`
  * `chunks=dims` size of the individual array chunks, must be a tuple of length `length(dims)`
  * `fill_value=nothing` value to represent missing values
  * `fill_as_missing=false` set to `true` shall fillvalue s be converted to `missing`s
  * `filters`=filters to be applied
  * `compressor=BloscCompressor()` compressor type and properties
  * `attrs=Dict()` a dict containing key-value pairs with metadata attributes associated to the array
  * `writeable=true` determines if the array is opened in read-only or write mode
