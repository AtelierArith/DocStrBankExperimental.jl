```
disable_logging(level)
```

Désactive tous les messages de journalisation à des niveaux de journalisation égaux ou inférieurs à `level`.  Il s'agit d'un paramètre *global*, destiné à rendre la journalisation de débogage extrêmement peu coûteuse lorsqu'elle est désactivée.

# Exemples

```julia
Logging.disable_logging(Logging.Info) # Désactiver le débogage et les informations
```
