```
fetch(t::Task)
```

Attendez qu'une [`Task`](@ref) se termine, puis renvoyez sa valeur de résultat. Si la tâche échoue avec une exception, une [`TaskFailedException`](@ref) (qui enveloppe la tâche échouée) est levée.
