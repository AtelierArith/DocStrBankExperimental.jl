```
zip_test(r::ZipReader)::Nothing
```

Test all entries in the archive in order from `1` to `zip_nentries(r)` Throw an error for the first invalid entry.
