```
zip_compression_method(x::HasEntries, i::Integer)::UInt16
```

Return the compression method used for entry `i`.

See https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT for a current list of methods.

Only Store(0), Deflate(8), and Deflate64(9) are supported for now.

Note: if the zip file was corrupted, this might be wrong.
