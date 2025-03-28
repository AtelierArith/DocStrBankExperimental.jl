```
errno([code])
```

Obtenez la valeur de `errno` de la bibliothèque C. Si un argument est spécifié, il est utilisé pour définir la valeur de `errno`.

La valeur de `errno` n'est valide qu'immédiatement après un `ccall` à une routine de bibliothèque C qui la définit. En particulier, vous ne pouvez pas appeler `errno` à l'invite suivante dans un REPL, car beaucoup de code est exécuté entre les invites.
