```
RadioMenu
```

Un menu qui permet à un utilisateur de sélectionner une seule option dans une liste.

# Sortie d'exemple

```julia-repl
julia> request(RadioMenu(options, pagesize=4))
Choisissez votre fruit préféré :
^  raisin
   fraise
 > myrtille
v  pêche
Votre fruit préféré est myrtille !
```
