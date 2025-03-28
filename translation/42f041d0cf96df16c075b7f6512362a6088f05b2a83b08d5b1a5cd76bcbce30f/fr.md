```
SpinLock()
```

Créez un verrou à spin non réentré, test-et-teste-et-établit. Une utilisation récursive entraînera un blocage. Ce type de verrou ne doit être utilisé que autour de code qui prend peu de temps à s'exécuter et ne bloque pas (par exemple, effectuer des E/S). En général, [`ReentrantLock`](@ref) devrait être utilisé à la place.

Chaque [`lock`](@ref) doit être associé à un [`unlock`](@ref). Si [`!islocked(lck::SpinLock)`](@ref islocked) est vrai, [`trylock(lck)`](@ref trylock) réussit à moins qu'il n'y ait d'autres tâches tentant de détenir le verrou "en même temps".

Les verrous à spin test-et-teste-et-établit sont les plus rapides jusqu'à environ 30 threads en concurrence. Si vous avez plus de concurrence que cela, d'autres approches de synchronisation devraient être envisagées.
