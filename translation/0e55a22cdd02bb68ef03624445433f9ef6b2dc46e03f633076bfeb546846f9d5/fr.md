```
default(p::Period) -> Period
```

Retourne une valeur "par défaut" sensée pour la période d'entrée en retournant `T(1)` pour l'Année, le Mois et le Jour, et `T(0)` pour l'Heure, la Minute, la Seconde et la Milliseconde.
