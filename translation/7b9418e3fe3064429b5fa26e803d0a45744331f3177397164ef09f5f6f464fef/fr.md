```
iterate(iter [, state]) -> Union{Nothing, Tuple{Any, Any}}
```

Faites avancer l'itérateur pour obtenir le prochain élément. Si aucun élément ne reste, `nothing` doit être retourné. Sinon, un tuple de 2 éléments contenant le prochain élément et le nouvel état d'itération doit être retourné.
