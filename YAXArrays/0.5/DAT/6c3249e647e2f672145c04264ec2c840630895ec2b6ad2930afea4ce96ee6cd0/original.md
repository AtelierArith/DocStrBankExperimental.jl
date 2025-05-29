```
CubeTable()
```

Function to turn a DataCube object into an iterable table. Takes a list of as arguments, specified as a `name=cube` expression. For example `CubeTable(data=cube1,country=cube2)` would generate a Table with the entries `data` and `country`, where `data` contains the values of `cube1` and `country` the values of `cube2`. The cubes are matched and broadcasted along their axes like in `mapCube`.
