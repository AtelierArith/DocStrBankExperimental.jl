```
zipsink(fname; [keyword arguments]) -> ZipArchiveSink
zipsink(io; [keyword arguments]) -> ZipArchiveSink
zipsink(f, args...)
```

Open an `IO` stream of a Zip archive for writing data.

# Positional arguments

  * `fname::AbstractString`: The name of a Zip archive file to open for writing. Will be created if the file does not exist. If the file does exist, it will be truncated before writing.
  * `io::IO`: An `IO` object that can be written to. The object will be closed when you call `close` on the returned object.
  * `f<:Function`: A unary function to which the opened stream will be passed. This method signature allows for `do` block usage. When called with the signature, the return value of `f` will be returned to the user.

# Keyword arguments

  * `utf8::Bool=true`: Encode file names and comments with UTF-8 encoding. If `false`, follows the Zip standard of treating text as encoded in IBM437 encoding.
  * `comment::AbstractString=""`: A comment to store with the Zip archive. This information is stored in plain text at the end of the archive and does not affect the Zip archive in any other way. The comment is always stored using IBM437 encoding.

!!! note "Using IO arguments"
    Passing an `IO` object as the first argument will use the object as-is, overwriting from the current position of the stream and writing the Central Directory after closing the stream without truncating the remainder. This use of `zipsink` is recommended for advanced users only who need to write Zip archives to write-only streams (e.g., network pipes).

