```
`set_paths("path_to_data", print_paths=true)`
```

Sets all paths in `rc[:paths]` relative to `path_to_data`.  Paths follow the standard format of `rc[:paths][:foo] = "path_to_data/foo"`, except for `rc[:paths][:data]` which is `"path_to_data"`. Warnings are issued if any chosen paths are not valid folders.

# Arguments

  * `path_to_data::AbstractString` : an absolute or relative path to use as the root of the data folder tree. Defaults to present working directory.
  * `print_paths::Bool` : Optional.  If `true`, prints contents of `rc[:paths]` to console.  Defaults to `false`.
  * `no_warn::Bool` : Optional.  Set `true` to suppress invalid path warnings.  Default to `false`.
