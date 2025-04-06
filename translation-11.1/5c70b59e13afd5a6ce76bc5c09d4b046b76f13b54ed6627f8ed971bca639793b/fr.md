```
lock(lock)
```

Acquérir le `lock` lorsqu'il devient disponible. Si le verrou est déjà verrouillé par une autre tâche/fil, attendez qu'il devienne disponible.

Chaque `lock` doit être associé à un [`unlock`](@ref).
