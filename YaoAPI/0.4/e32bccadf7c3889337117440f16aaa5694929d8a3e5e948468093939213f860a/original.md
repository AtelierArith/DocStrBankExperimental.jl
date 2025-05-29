```
fidelity(register1, register2) -> Real/Vector{<:Real}
fidelity'(pair_or_reg1, pair_or_reg2) -> (g1, g2)
```

Return the fidelity between two states. Calcuate the fidelity between `r1` and `r2`, if `r1` or `r2` is not pure state (`nactive(r) != nqudits(r)`), the fidelity is calcuated by purification. See also: http://iopscience.iop.org/article/10.1088/1367-2630/aa6a4b/meta

Obtain the gradient with respect to registers and circuit parameters. For pair input `ψ=>circuit`, the returned gradient is a pair of `gψ=>gparams`, with `gψ` the gradient of input state and `gparams` the gradients of circuit parameters. For register input, the return value is a register.

### Definition

The fidelity of two quantum state for qudits is defined as:

$$
F(ρ, σ) = tr(\sqrt{\sqrt{ρ}σ\sqrt{ρ}})
$$

!!! note
    This definition is different from [the one in Wiki](https://en.wikipedia.org/wiki/Fidelity_of_quantum_states) by a square.


### Examples

```jldoctest; setup=:(using Yao)
julia> reg1 = uniform_state(3);

julia> reg2 = zero_state(3);

julia> fidelity(reg1, reg2)
0.35355339059327373
```

### References

  * Jozsa R. Fidelity for mixed quantum states[J]. Journal of modern optics, 1994, 41(12): 2315-2323.
  * Nielsen M A, Chuang I. Quantum computation and quantum information[J]. 2002.

!!! note
    The original definition of fidelity $F$ was from "transition probability", defined by Jozsa in 1994, it is the square of what we use here.

