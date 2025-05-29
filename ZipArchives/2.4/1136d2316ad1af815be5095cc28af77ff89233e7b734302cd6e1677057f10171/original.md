```
zip_openentry(r::ZipReader, i::Union{AbstractString, Integer})
zip_openentry(f::Function, r::ZipReader, i::Union{AbstractString, Integer})
```

Open entry `i` from `r` as a readable IO.

If `i` is a string open the last entry with the exact matching name.

Make sure to close the returned stream when done reading,  if not using the do block method.

The stream returned by this function should only be accessed by one thread at a time.

See also [`zip_readentry`](@ref).
