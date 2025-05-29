```
write_file(sink, fname, data; [keyword arguments])
```

Archive `data` to a new file named `fname` in an archive sink all at once.

This is a convenience method that will create a new file in the archive with name `fname` and write all of `data` to that file. The `data` argument can be anything for which the method `write(io, data)` is defined.

Returns the number of bytes written to the archive.

Keyword arguments are the same as those accepted by [`open(::ZipArchiveSink, ::AbstractString)`](@ref).

!!! note "Memory requirements"
    This method reads `data` into a buffer before writing it to the archive. Both `data` and the buffered (potentially compressed) copy must be able to fit into memory simultaneously.

