```
zip_test_entry(x::ZipReader, i::Integer)::Nothing
```

If entry `i` has an issue, error. Otherwise, return nothing.

This will also read the entry and check the crc32 matches.
