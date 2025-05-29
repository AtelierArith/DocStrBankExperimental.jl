```
is_valid!([sink::IO,] source::ZipArchiveSource) -> Bool
```

Validate the files in the archive `source` against the Central Directory at the end of the archive.

The exclaimation mark in the function name is a warning to the user that this method consumes *all* the remaining data from `source`. and returns `false` if the file information from the file headers read does not match the information in the Central Directory. Files that have already been consumed prior to calling this method will still be validated, but the local headers of those files will *not* be validated against the local data that has already been consumed.

The exclaimation mark in the function name is a warning to the user that the function destructively reads bytes from the `ZipArchiveSource`. If `sink` is provided, the remaining unread bytes from `source` will be extracted and the data from the remaining files will be written as concatenated bytes into `sink`.

Because data cannot be written to a `ZipArchiveSource`, repeated calls to `is_valid!` will return the same result each time, but will only extract data to `sink` on the first call.

!!! warning "Files using descriptors"
    If a file stored within `source` uses a File Descriptor rather than storing the size of the file in the Local File Header, the file must be read to the end in order to properly record the lengths for checking against the Central Directory. Failure to read such a file to the end will result in `is_valid!` returning `false` when called on the archive.


See also [`is_valid!(::ZipFileSource)`](@ref).
