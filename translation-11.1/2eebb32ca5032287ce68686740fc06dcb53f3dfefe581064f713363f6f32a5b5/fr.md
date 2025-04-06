```
lookup(pointer::Ptr{Cvoid}) -> Vector{StackFrame}
```

Étant donné un pointeur vers un contexte d'exécution (généralement généré par un appel à `backtrace`), recherche des informations de contexte de cadre de pile. Renvoie un tableau d'informations de cadre pour toutes les fonctions en ligne à ce moment-là, la fonction la plus interne en premier.
