```
apropos([io::IO=stdout], pattern::Union{AbstractString,Regex})
```

Recherchez les docstrings disponibles pour les entrées contenant `pattern`.

Lorsque `pattern` est une chaîne, la casse est ignorée. Les résultats sont imprimés dans `io`.

`apropos` peut être appelé depuis le mode d'aide dans le REPL en entourant la requête de guillemets doubles :

```
help?> "pattern"
```
