```
lowrankupdowndate!(F::CHOLMOD.Factor, C::Sparse, update::Cint)
```

Met à jour une factorisation `LDLt` ou `LLt` `F` de `A` à une factorisation de `A ± C*C'`.

Si une factorisation préservant la sparsité est utilisée, c'est-à-dire `L*L' == P*A*P'`, alors le nouveau facteur sera `L*L' == P*A*P' + C'*C`

`update`: `Cint(1)` pour `A + CC'`, `Cint(0)` pour `A - CC'`
