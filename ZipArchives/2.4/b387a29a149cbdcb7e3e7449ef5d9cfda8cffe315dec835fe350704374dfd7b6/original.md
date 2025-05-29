```
zip_entry_data_offset(r::ZipReader, i::Integer)::Int64
```

Return the offset of the start of the compressed data for entry `i` from the start of the buffer in `r`.

Throw an error if the local header is invalid.

See also [`zip_compression_method`](@ref) and [`zip_compressed_size`](@ref).
