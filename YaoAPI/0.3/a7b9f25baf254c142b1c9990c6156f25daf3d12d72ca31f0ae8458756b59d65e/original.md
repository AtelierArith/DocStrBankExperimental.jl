```
apply_back!((ψ, ∂L/∂ψ*), circuit::AbstractBlock, collector) -> AbstractRegister
```

back propagate and calculate the gradient ∂L/∂θ = 2*Re(∂L/∂ψ*⋅∂ψ*/∂θ), given ∂L/∂ψ*. `ψ` is the output register, ∂L/∂ψ* should also be register type.

Note: gradients are stored in `Diff` blocks, it can be access by either `diffblock.grad` or `gradient(circuit)`. Note2: now `apply_back!` returns the inversed gradient!
