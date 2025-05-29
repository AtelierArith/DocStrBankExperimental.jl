```
hilbertkron(num_bit::Int, gates::Vector{AbstractMatrix}, locs::Vector{Int}; nlevel=2) -> AbstractMatrix
```

Return general kronecher product form of gates in Hilbert space of `num_bit` qudits.

  * `gates` are a list of matrices.
  * `start_locs` should have the same length as `gates`, specifing the gates starting positions.
