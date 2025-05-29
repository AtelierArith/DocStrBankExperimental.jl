```
next_file(archive) => Union{IO, Nothing}
```

Read the next file in the archive and return a readable `IO` object or `nothing`.

This is the same as calling `first(iterate(archive))`.
