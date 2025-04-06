```
chown(path::AbstractString, owner::Integer, group::Integer=-1)
```

Change le propriétaire et/ou le groupe de `path` en `owner` et/ou `group`. Si la valeur saisie pour `owner` ou `group` est `-1`, l'ID correspondant ne changera pas. Seuls les `owner`s et `group`s de type entier sont actuellement pris en charge. Retourne `path`.
