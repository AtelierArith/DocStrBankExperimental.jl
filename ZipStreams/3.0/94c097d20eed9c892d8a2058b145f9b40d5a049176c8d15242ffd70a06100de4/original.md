```
zip_files(out_filename, files; [keyword_args])
zip_files(out_filename, dir; recurse_directories=false, [keyword_args])
```

Create an archive from files on disk.

The archive `out_filename` will be created using the `zipsink` method with the keyword arguments split as listed below. `in_filename` can be a single path or a vector of multiple paths on disk. The files will be written in the archive with paths matching the closest common relative path between the current directory (`"."`) and the full path of the file, so if `archive_filename` is "/a/b/archive.zip" and one of `files` is "/a/c/file", then the file will be witten with the path "c/file".

If `dir` is a directory and `recurse_directories` is `true`, then all files and directories found when traversing the directory will be added to the archive. If `recurse_directories` is `false` (the default), then subdirectories of `dir` will not be traversed.

All files are written to the archive using the default arguments specified by `open(zipsink, fn; keyword_args..)`, with special keyword arguments split as described below.

# Arguments

  * `out_filename::AbstractString`: the output archive filename to create.
  * `files::AbstractVector{<:AbstractString}`: a list of file paths to add to the newly   created archive.
  * `dir::AbstractString`: a path to a directory to add to the newly created archive.

# Keyword arguments

  * `utf8::Bool = true`: use UTF-8 encoding for file names and comments (if `false`, use   IBM437).
  * `archive_comment::AbstractString = ""`: archive comment string to add to the central   directory, equivalent to passing the `comment` keyword to `zipsink`.
  * `file_options::Dict{String, Any} = nothing`: if a file name added to the archive *exactly*   matches (`==`) a key in `file_options`, then the value corresponding to that key will be   splatted as keyword arguments for that file only, overriding keyword arguments passed as   described below.
  * All other keyword arguments: passed unmodified to the `open(sink, filename)` method.

See [`open(::ZipArchiveSink, ::AbstractString)`](@ref) and [`zipsink`](@ref) for more information about the optional keyword arguments available for each method.
