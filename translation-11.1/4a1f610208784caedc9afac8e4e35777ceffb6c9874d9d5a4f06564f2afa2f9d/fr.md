```
current_exceptions(task::Task=current_task(); [backtrace::Bool=true])
```

Obtenez la pile des exceptions actuellement gérées. Pour les blocs catch imbriqués, il peut y avoir plus d'une exception actuelle, auquel cas l'exception lancée le plus récemment est la dernière dans la pile. La pile est renvoyée sous la forme d'un `ExceptionStack`, qui est un AbstractVector de tuples nommés `(exception,backtrace)`. Si `backtrace` est faux, la trace de la pile dans chaque paire sera définie sur `nothing`.

Passer explicitement `task` renverra la pile d'exceptions actuelle sur une tâche arbitraire. Cela est utile pour inspecter les tâches qui ont échoué en raison d'exceptions non interceptées.

!!! compat "Julia 1.7"
    Cette fonction était connue sous le nom expérimental de `catch_stack()` dans Julia 1.1–1.6, et avait un type de retour de Vector de tuples simple.

