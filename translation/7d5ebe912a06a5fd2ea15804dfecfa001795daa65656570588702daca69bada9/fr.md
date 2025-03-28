```
__precompile__(isprecompilable::Bool)
```

Spécifiez si le fichier appelant cette fonction est précompilable, par défaut `true`. Si un module ou un fichier n'est *pas* sûr de pouvoir être précompilé, il doit appeler `__precompile__(false)` afin de générer une erreur si Julia tente de le précompiler.
