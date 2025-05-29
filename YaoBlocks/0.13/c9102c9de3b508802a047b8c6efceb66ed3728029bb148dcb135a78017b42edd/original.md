A control block is a composite block that applies a block when the control qubits are all ones.

!!! note
    If control qubit index is negative, it means the inverse control, i.e., the block is applied when the control qubit is zero.


### Fields

  * `n::Int64`
  * `ctrl_locs::NTuple{C, Int64} where C`
  * `ctrl_config::NTuple{C, Int64} where C`
  * `content::YaoAPI.AbstractBlock`
  * `locs::NTuple{M, Int64} where M`
