```
control(n, ctrl_locs, locations => subblock)
```

Return a `n`-qubit [`ControlBlock`](@ref), where the control locations `ctrl_locs` and the subblock `locations` in the third argument can be an integer, a tuple or a range, and the size of the subblock should match the length of `locations`. Let $I$ be the $2 \times 2$ identity matrix, $G$ be a $2 \times 2$ subblock, $P_0=|0\rangle\langle 0|$ and $P_1=|1\rangle\langle 1|$ be two single qubit projection operators to subspace $|0\rangle$ and $|1\rangle$, $i$ and $j$ be two integers that $i>j$. The matrix representation of `control(n, i, j=>G)` is

$$
\begin{align}
&I^{\otimes n-i} P_0 \otimes I^{\otimes i-j-1} \otimes I\otimes I^{\otimes j-1}
+\\
& I^{\otimes n-i} P_1 \otimes I^{\otimes i-j-1} \otimes G\otimes I^{\otimes j-1}
\end{align}
$$

The multi-controlled multi-qubit controlled block is more complicated, it means apply the gate when control qubits are all ones. Each control location can take a negative sign to represent the inverse control, meaning only when this qubit is `0`, the controlled gate is applied.

### Examples

```jldoctest; setup=:(using Yao)
julia> control(4, (1, 2), 3=>X)
nqubits: 4
control(1, 2)
└─ (3,) X

julia> control(4, 1, 3=>X)
nqubits: 4
control(1)
└─ (3,) X
```
