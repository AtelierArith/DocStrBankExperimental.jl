```
zip_definitely_utf8(x::HasEntries, i::Integer)::Bool
```

Return true if entry `i` name is marked as utf8 or is ascii.

Otherwise, the name should probably be treated as a sequence of bytes.

This package will never attempt to transcode filenames.
