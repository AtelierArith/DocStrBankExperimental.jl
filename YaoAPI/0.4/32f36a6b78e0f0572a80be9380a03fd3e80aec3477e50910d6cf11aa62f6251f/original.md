```
operator_fidelity(b1::AbstractBlock, b2::AbstractBlock) -> Number
```

Operator fidelity defined as

$$
F(A, B) = \frac{1}{d}|{\rm Tr}(A^\dagger B)|
$$

Here, `d` is the size of the Hilbert space. Note this quantity is independant to global phase. See arXiv: 0803.2940v2, Equation (2) for reference.

### Examples

```jldoctest; setup=:(using Yao)
julia> operator_fidelity(X, X)
1.0

julia> operator_fidelity(X, Z)
0.0
```
