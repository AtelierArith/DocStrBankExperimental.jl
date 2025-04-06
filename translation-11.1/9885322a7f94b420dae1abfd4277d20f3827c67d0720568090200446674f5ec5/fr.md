```
unlock(lock)
```

Libère la propriété du `lock`.

Si c'est un verrou récursif qui a été acquis auparavant, décrémentez un compteur interne et retournez immédiatement.
