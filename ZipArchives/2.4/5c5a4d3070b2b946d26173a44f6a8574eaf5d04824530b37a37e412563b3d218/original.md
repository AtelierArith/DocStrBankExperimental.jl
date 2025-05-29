```
zip_commitfile(w::ZipWriter)
```

Close any open entry making `w` not writable. If there is some error, this will behave like [`zip_abortfile`](@ref) then rethrow the error.
