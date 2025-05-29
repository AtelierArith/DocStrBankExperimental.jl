```
operator_fidelity(b1::AbstractBlock, b2::AbstractBlock) -> Number
```

Operator fidelity defined as

$$
F^2 = \frac{1}{d^2}\left[{\rm Tr}(b1^\dagger b2)\right]
$$

Here, `d` is the size of the Hilbert space. Note this quantity is independant to global phase. See arXiv: 0803.2940v2, Equation (2) for reference.
