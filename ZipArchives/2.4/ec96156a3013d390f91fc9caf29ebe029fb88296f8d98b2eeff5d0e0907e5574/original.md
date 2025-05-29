```
zip_readentry(r::ZipReader, i::Union{AbstractString, Integer}, args...; kwargs...)
```

Read the contents of entry `i` in `r`.

If `i` is a string read the last entry with the exact matching name.

`args...; kwargs...` are passed on to `read` after the entry `i` in zip reader `r` is opened with [`zip_openentry`](@ref)

if `args...` are empty or `String`, this will also error if the checksum doesn't match.

See also [`zip_openentry`](@ref).
