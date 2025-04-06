```
isdispatchtuple(T)
```

Déterminez si le type `T` est un "type feuille" de tuple, ce qui signifie qu'il pourrait apparaître comme une signature de type dans le dispatch et n'a pas de sous-types (ou super-types) qui pourraient apparaître dans un appel. Si `T` n'est pas un type, alors retournez `false`.
