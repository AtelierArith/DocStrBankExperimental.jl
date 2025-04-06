```
get_zero_subnormals() -> Bool
```

Retourne `false` si les opérations sur les valeurs flottantes subnormales ("denormals") respectent les règles de l'arithmétique IEEE, et `true` si elles pourraient être converties en zéros.

!!! avertissement
    Cette fonction n'affecte que le thread actuel.

