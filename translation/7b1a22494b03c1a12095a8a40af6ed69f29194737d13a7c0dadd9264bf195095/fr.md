```
LogLevel(niveau)
```

Gravité/verbosité d'un enregistrement de journal.

Le niveau de journal fournit une clé contre laquelle les enregistrements de journal potentiels peuvent être filtrés, avant que tout autre travail ne soit effectué pour construire la structure de données de l'enregistrement de journal lui-même.

# Exemples

```julia-repl
julia> Logging.LogLevel(0) == Logging.Info
true
```
