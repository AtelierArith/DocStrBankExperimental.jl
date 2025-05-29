```
zip_stored_crc32(x::HasEntries, i::Integer)::UInt32
```

Return the marked crc32 of entry `i` in the central directory.

Note: if the zip file was corrupted, this might be wrong.

See also [`zip_crc32`](@ref), [`zip_test_entry`](@ref).
