```
lowrankupdowndate!(F::CHOLMOD.Factor, C::Sparse, update::Cint)
```

Aktualisieren Sie eine `LDLt`- oder `LLt`-Faktorisierung `F` von `A` zu einer Faktorisierung von `A ± C*C'`.

Wenn eine spärlichkeitserhaltende Faktorisierung verwendet wird, d.h. `L*L' == P*A*P'`, dann wird der neue Faktor `L*L' == P*A*P' + C'*C`

`update`: `Cint(1)` für `A + CC'`, `Cint(0)` für `A - CC'`
