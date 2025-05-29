```
reorder!(reigster, orders)
```

Reorder the locations of register by input orders. For a 3-qubit register, an order `(i, j, k)` specifies the following reordering of qubits

  * move the first qubit go to `i`,
  * move the second qubit go to `j`,
  * move the third qubit go to `k`.

!!! note
    The convention of `reorder!` is different from the `permutedims` function, one can use the `sortperm` function to relate the permutation order and the order in this function.


### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"010101");

julia> reorder!(reg, (1,4,2,5,3,6));

julia> measure(reg)
1-element Vector{DitStr{2, 6, Int64}}:
 000111 ₍₂₎
```
