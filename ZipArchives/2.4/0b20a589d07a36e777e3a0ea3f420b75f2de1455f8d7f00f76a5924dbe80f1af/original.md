```
zip_newfile(w::ZipWriter, name::AbstractString; 
    compress::Bool=false,
)
```

Start a new file entry named `name`.

This will commit any currently open entry  and make `w` writable for file entry `name`.

The underlying `IO` in `w` must be seekable to use this function. If not see [`zip_writefile`](@ref)

# Optional Keywords

  * `comment::String=""`: Entry comment, `ncodeunits(comment) ≤ typemax(UInt16)`.
  * `compress::Bool=false`:    If false no compression is used and other compression options are ignored.
  * `compression_level::Int=-1`:   1 is fastest, 9 is smallest file size.    0 is no compression, and -1 is a good compromise between speed and file size.
  * `compression_method=Deflate`: Currently only `Deflate` and `Store` are supported.
  * `executable::Union{Nothing,Bool}=nothing`: Set to true to mark file as executable.   Defaults to false.
  * `external_attrs::Union{Nothing,UInt32}=nothing`: Manually override the    external file attributes: See https://unix.stackexchange.com/questions/14705/the-zip-formats-external-file-attribute
