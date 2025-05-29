```
zipsource(io)
zipsource(f, io)
```

Create a read-only lazy streamable representation of a Zip archive.

The first form returns a `ZipArchiveSource` wrapped around `io` that allows the user to extract files as they are read from the stream by iterating over the returned object. `io` can be an object that inherits from `Base.IO` (technically only requiring `read`, `eof`, `isopen`, `close`, and `bytesavailable` to be defined) or an `AbstractString` file name, which will open the file in read-only mode and wrap that `IOStream`.

The second form takes a unary function as the first argument. The constructed `ZipArchiveSource` object will be passed to the function and the results of the function will be returned to the user. This allows compatability with `do` blocks. If `io` is an `AbstractString` file name, the file will be automatically closed when the block exits. If `io` is a `Base.IO` object as described above, it will *not* be closed when the block exits, allowing the caller to have control over the lifetime of the argument.

!!! warning "Reading before knowing where files end can be dangerous!"
    The Central Directory in the Zip archive is the *authoritative source* for file locations, compressed and uncompressed sizes, and CRC-32 checksums. A Local File Header can lie about this information, leading to improper file extraction.  We **highly** recommend that users validate the file contents against the Central Directory using the `is_valid!` method before beginning to trust the extracted files from uncontrolled sources.

