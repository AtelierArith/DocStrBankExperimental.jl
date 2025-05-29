```
fidelity(register1, register2)
```

Return the fidelity between two states.

# Definition

The fidelity of two quantum state for qudits is defined as:

$$
F(ρ, σ) = tr(\sqrt{\sqrt{ρ}σ\sqrt{ρ}})
$$

Or its equivalent form (which we use in numerical calculation):

$$
F(ρ, σ) = sqrt(tr(ρσ) + 2 \sqrt{det(ρ)det(σ)})
$$

# Reference

  * Jozsa R. Fidelity for mixed quantum states[J]. Journal of modern optics, 1994, 41(12): 2315-2323.
  * Nielsen M A, Chuang I. Quantum computation and quantum information[J]. 2002.

!!! note
    The original definition of fidelity $F$ was from "transition probability", defined by Jozsa in 1994, it is the square of what we use here.

