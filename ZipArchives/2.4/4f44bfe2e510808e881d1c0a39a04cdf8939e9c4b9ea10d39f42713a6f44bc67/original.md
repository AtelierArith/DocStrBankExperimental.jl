```
zip_compressed_size(x::HasEntries, i::Integer)::UInt64
```

Return the marked compressed size of entry `i` in number of bytes.

Note: if the zip file was corrupted, this might be wrong.
