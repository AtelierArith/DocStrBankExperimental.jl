```
zip_writefile(w::ZipWriter, name::AbstractString, data::AbstractVector{UInt8})
```

Write data as a file entry named `name`.

Unlike `zip_newfile`, the underlying IO only needs to implement  `Base.unsafe_write` and `Base.isopen`. `w` isn't writable after. The written data will not be compressed.

See also, [`zip_newfile`](@ref)

# Optional Keywords

  * `comment::String=""`: Entry comment, `ncodeunits(comment) ≤ typemax(UInt16)`.
  * `executable::Union{Nothing,Bool}=nothing`: Set to true to mark file as executable.   Defaults to false.
  * `external_attr::Union{Nothing,UInt32}=nothing`: Manually set the    external file attributes: See https://unix.stackexchange.com/questions/14705/the-zip-formats-external-file-attribute
