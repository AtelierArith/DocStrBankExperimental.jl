```
CachedBlock{ST, BT, D} <: TagBlock{BT, D}
```

A label type that tags an instance of type `BT`. It forwards every methods of the block it contains, except [`mat`](@ref) and [`apply!`](@ref), it will cache the matrix form whenever the program has.
