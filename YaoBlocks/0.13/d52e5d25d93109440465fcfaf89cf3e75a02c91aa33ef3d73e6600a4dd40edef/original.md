```
ReflectGate{D, T, Tt, AT<:AbstractArrayReg{D, T}} = TimeEvolution{D,Tt,Projector{D,T,AT}}
```

Let `|v⟩` be a quantum state vector, a reflection gate is a unitary operator that defined as the following operation.

$$
|v⟩ → 1 - (1-exp(-iθ)) |v⟩⟨v|
$$

When $θ = π$, it defines a standard reflection gate $1-2|v⟩⟨v|$.
