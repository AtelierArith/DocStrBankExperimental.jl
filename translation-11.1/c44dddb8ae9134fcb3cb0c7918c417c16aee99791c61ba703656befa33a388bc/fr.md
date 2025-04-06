```
Base.checked_length(r)
```

Calcule `length(r)`, mais peut vérifier les erreurs de dépassement lorsque le résultat ne peut pas être contenu dans `Union{Integer(eltype(r)),Int}`.
