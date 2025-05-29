```
Locations <: AbstractLocations
```

Type to annotate locations in quantum circuit.

```
Locations(x)
```

Create a `Locations` object from a raw location statement. Valid storage types are:

  * `Int`: single position
  * `NTuple{N, Int}`: a list of locations
  * `UnitRange{Int}`: contiguous locations

Other types will be converted to the storage type via `Tuple`.
