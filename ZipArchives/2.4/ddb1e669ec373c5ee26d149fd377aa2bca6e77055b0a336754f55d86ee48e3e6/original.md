```
zip_append_archive(io::IO; trunc_footer=true, zip_kwargs=(;))::ZipWriter
```

Return a `ZipWriter` that will add entries to the existing zip archive in `io`.

This also works with a `filename::AbstractString` instead of an `io::IO`. In that case, all passed keyword arguments will be used for  `Base.open` in addition to `read=true, write=true`.

If `io` doesn't have a valid zip archive footer already, this function will error.

If `trunc_footer=true` the no longer needed zip archive footer at the end of `io` will be truncated. Otherwise, it will be left as is.

`zip_kwargs` will be forwarded to [`ZipWriter`](@ref)
