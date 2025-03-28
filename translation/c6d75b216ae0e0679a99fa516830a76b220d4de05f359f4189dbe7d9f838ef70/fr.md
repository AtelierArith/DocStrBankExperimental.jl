```
Base.checked_neg(x)
```

Calcule `-x`, en vérifiant les erreurs de débordement lorsque cela est applicable. Par exemple, les entiers signés en complément à deux standard (par exemple, `Int`) ne peuvent pas représenter `-typemin(Int)`, ce qui entraîne un débordement.

La protection contre le débordement peut imposer une pénalité de performance perceptible.
