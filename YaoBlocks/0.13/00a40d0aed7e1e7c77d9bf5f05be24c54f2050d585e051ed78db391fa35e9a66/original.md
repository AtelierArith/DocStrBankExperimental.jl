```
two_qubit_depolarizing_channel(p::Real)
```

Create a two-qubit depolarizing channel. Note that this is not the same  as `kron(single_qubit_depolarizing_channel(p), single_qubit_depolarizing_channel(p))`.
