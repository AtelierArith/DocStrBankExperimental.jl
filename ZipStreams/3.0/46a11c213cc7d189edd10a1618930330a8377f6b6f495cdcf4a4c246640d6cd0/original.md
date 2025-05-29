```
unzip_files(archive; output_path::AbstractString=".", make_path::Bool=false)
unzip_files(archive, files; [keyword_args])
```

Unzip `files` from `archive`. If `files` is not given, extract all files.

This method opens the archive and iterates through the archived files, writing them to disk to the directory tree rooted at `output_path`. If `make_path` is `true` and `output_path` does not exist, it will be created.

See [`zipsource`](@ref) and [`next_file`](@ref) for more information about how the files are read from the archive.
