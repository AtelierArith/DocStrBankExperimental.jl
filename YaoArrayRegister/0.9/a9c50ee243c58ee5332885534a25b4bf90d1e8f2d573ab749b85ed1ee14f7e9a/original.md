```
mutual_information(register_or_rho, part1, part2)
```

Returns the mutual information between subsystems `part1` and `part2` of the input quantum register or density matrix:

$$
S(\rho_A) + S(\rho_B) - S(\rho_{AB})
$$

### Example

The mutual information of a GHZ state of any two disjoint parts is always equal to $\log 2$.

```jldoctest; setup=:(using Yao)
julia> mutual_information(ghz_state(4), (1,), (3,4))
0.6931471805599132
```
