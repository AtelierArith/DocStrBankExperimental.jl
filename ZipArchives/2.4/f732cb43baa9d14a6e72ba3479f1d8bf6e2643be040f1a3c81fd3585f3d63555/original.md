```
zip_mkdir(w::ZipWriter, name::AbstractString)
```

Write a directory entry named `name`.

`name` should end in "/". If not, a "/" will be appended.

This is only needed to add an empty directory.
