```
transpose(F::Faktorisierung)
```

Faulheitstransposition der Faktorisierung `F`. Gibt standardmäßig eine [`TransposeFactorization`](@ref) zurück, es sei denn, es handelt sich um `Faktorisierungen` mit reellem `eltype`, in diesem Fall wird eine [`AdjointFactorization`](@ref) zurückgegeben.
