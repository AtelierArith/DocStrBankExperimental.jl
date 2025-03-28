```
systemsleep(s::Real)
```

Suspend l'exécution pendant `s` secondes. Cette fonction ne cède pas au planificateur de Julia et bloque donc le fil Julia sur lequel elle s'exécute pendant la durée du temps de sommeil.

Voir aussi [`sleep`](@ref).
