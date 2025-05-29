```
getdata(x)
```

Returns a handle to the raw data of the array, which can be indexed as a normal Julia Array. This might return the object itself, but ideally if returns only the AbstractArray/DiskArray wrapped by the type.
