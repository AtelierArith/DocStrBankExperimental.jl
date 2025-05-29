```
instruct!([nlevel=Val(2), ]state, operator, locs[, control_locs, control_configs, theta])
```

Unified interface for applying an operator to a quantum state. It modifies the `state` directly.

### Arguments

  * `nlevel` is the number of levels in each qudit,
  * `state` is a vector or matrix representing the quantum state, where the first dimension is the active qubit dimension, the second is the batch dimension.
  * `operator` is a quantum operator, which can be `Val(GATE_SYMBOL)` or a matrix.
  * `locs::Tuple` is a tuple for specifying the locations this gate applied.
  * `control_locs::Tuple` and `control_configs` are tuples for specifying the control locations and control values.
  * `theta::Real` is the parameter for the gate, e.g. `Val(:Rx)` gate takes a real number of its parameter.
