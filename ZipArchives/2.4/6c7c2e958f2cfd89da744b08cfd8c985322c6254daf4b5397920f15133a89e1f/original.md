```
mutable struct ZipWriter{S<:IO} <: IO
ZipWriter(io::IO; zip_kwargs...)::ZipWriter{typeof(io)}
ZipWriter(f::Function, io::IO; zip_kwargs...)::ZipWriter{typeof(io)}
```

Create a zip archive writer on `io`.

These methods also work with a `filename::AbstractString` instead of an `io::IO`.

In that case, all passed keyword arguments will be used for  `Base.open` in addition to `write=true`.

`io` must not be modified before the `ZipWriter` is closed (except using the wrapping `ZipWriter`).

The `ZipWriter` becomes a writable `IO` after a call to [`zip_newfile`](@ref)

```
zip_newfile(w::ZipWriter, name::AbstractString; newfile_kwargs...)
```

Any writes to the `ZipWriter` will write to the last specified new file.

If [`zip_newfile`](@ref) is called while `ZipWriter` is writable, the previous file is committed to the archive. There is no way to edit previously written data.

An alternative to [`zip_newfile`](@ref) is [`zip_writefile`](@ref)

```
zip_writefile(w::ZipWriter, name::AbstractString, data::AbstractVector{UInt8})
```

This will directly write a vector of data to a file entry in `w`. Unlike [`zip_newfile`](@ref) using [`zip_writefile`](@ref) doesn't require `io`  to be seekable.

`Base.close` on a `ZipWriter` will only close the wrapped `io` if `zip_kwargs` has `own_io=true` or the `ZipWriter` was created from a filename.

# Multi threading

A single `ZipWriter` instance doesn't allow mutations or  writes from multiple threads at the same time.

# Appending

`ZipWriter` assumes `io` is empty. Trying to write to an `io` with existing data will result in an invalid archive.

If you want to add entries to existing zip archive, use [`zip_append_archive`](@ref)

# Optional Keywords

  * `check_names::Bool=true`: Best attempt to error if new entry names aren't valid on windows    or already exist in the archive in a case insensitive way.
