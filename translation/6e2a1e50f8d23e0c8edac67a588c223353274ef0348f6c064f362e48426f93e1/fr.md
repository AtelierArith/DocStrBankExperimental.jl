```
Base.checked_abs(x)
```

Calcule `abs(x)`, en vérifiant les erreurs de dépassement lorsque cela est applicable. Par exemple, les entiers signés en complément à deux standard (par exemple, `Int`) ne peuvent pas représenter `abs(typemin(Int))`, ce qui entraîne un dépassement.

La protection contre le dépassement peut imposer une pénalité de performance perceptible.
