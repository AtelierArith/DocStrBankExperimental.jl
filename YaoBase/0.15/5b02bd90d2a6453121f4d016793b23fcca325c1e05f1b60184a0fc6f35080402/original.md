```
general_controlled_gates(num_bit::Int, projectors::Vector{Tp}, cbits::Vector{Int}, gates::Vector{AbstractMatrix}, locs::Vector{Int}) -> AbstractMatrix
```

Return general multi-controlled gates in hilbert space of `num_bit` qudits,

  * `projectors` are often chosen as `P0` and `P1` for inverse-Control and Control at specific position.
  * `cbits` should have the same length as `projectors`, specifing the controling positions.
  * `gates` are a list of controlled single qubit gates.
  * `locs` should have the same length as `gates`, specifing the gates positions.
