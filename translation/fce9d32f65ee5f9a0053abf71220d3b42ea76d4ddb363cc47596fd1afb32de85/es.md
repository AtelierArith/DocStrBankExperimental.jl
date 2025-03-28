```
lowrankupdowndate!(F::CHOLMOD.Factor, C::Sparse, update::Cint)
```

Actualiza una factorización `LDLt` o `LLt` `F` de `A` a una factorización de `A ± C*C'`.

Si se utiliza una factorización que preserva la esparsidad, es decir, `L*L' == P*A*P'`, entonces el nuevo factor será `L*L' == P*A*P' + C'*C`

`update`: `Cint(1)` para `A + CC'`, `Cint(0)` para `A - CC'`
