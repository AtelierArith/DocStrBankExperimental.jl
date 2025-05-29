```
time_evolve(H, dt[; tol=1e-7, check_hermicity=true])
```

Create a [`TimeEvolution`](@ref) block with Hamiltonian `H` and time step `dt`. The `TimeEvolution` block will use Krylove based `expv` to calculate time propagation. `TimeEvolution` block can also be used for [imaginary time evolution](http://large.stanford.edu/courses/2008/ph372/behroozi2/) if `dt` is complex. Let $H$ be a hamiltonian and $t$ be a time, the matrix representation of `time_evolve(H, t)` is $e^{-iHt}$.

### Arguments

  * `H` the hamiltonian represented as an `AbstractBlock`.
  * `dt`: the evolution duration (start time is zero).

### Keyword Arguments

  * `tol::Real=1e-7`: error tolerance.
  * `check_hermicity=true`: check hermicity or not.

### Examples

```jldoctest; setup=:(using Yao)
julia> time_evolve(kron(2, 1=>X, 2=>X), 0.1)
Time Evolution Δt = 0.1, tol = 1.0e-7
kron
├─ 1=>X
└─ 2=>X
```
