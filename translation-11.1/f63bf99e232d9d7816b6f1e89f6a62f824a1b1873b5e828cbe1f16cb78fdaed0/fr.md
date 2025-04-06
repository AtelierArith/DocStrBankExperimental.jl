```
trymkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
trymkpidlock(at::String, proc::Process; kwopts...)
```

Comme `mkpidlock` sauf qu'il retourne `false` au lieu d'attendre si le fichier est déjà verrouillé.

!!! compat "Julia 1.10"
    Cette fonction nécessite au moins Julia 1.10.

