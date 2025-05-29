```
zip_abortfile(w::ZipWriter)
```

Close any open entry making `w` not writable.

The open entry is not added to the list of entries  so will be ignored when the zip archive is read.
