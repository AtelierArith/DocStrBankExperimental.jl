```
struct ZipReader{T<:AbstractVector{UInt8}}
ZipReader(buffer::AbstractVector{UInt8})
```

View the bytes in `buffer` as a ZIP archive.

The array must not be modified while being read.

`zip_nentries(r::ZipReader)::Int` returns the number of entries in the archive.

`zip_names(r::ZipReader)::Vector{String}` returns the names of all the entries in the archive.

The following get information about an entry in the archive:

Entries are indexed from `1:zip_nentries(r)`

1. `zip_name(r::ZipReader, i::Integer)::String`
2. `zip_uncompressed_size(r::ZipReader, i::Integer)::UInt64`

`zip_test_entry(r::ZipReader, i::Integer)::Nothing` checks if an entry is valid and has a good checksum.

`zip_openentry` and `zip_readentry` can be used to read data from an entry.

The `parent` function can be used to get the underlying buffer.

# Multi threading

The returned `ZipReader` object can safely be used from multiple threads; however, the streams returned by `zip_openentry` should only be accessed by one thread at a time.
