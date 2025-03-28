```
tonext(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

Ajuste `dt` au prochain jour de la semaine correspondant à `dow` avec `1 = Lundi, 2 = Mardi, etc`. En définissant `same=true`, le `dt` actuel peut être considéré comme le prochain `dow`, permettant ainsi qu'aucun ajustement n'ait lieu.
