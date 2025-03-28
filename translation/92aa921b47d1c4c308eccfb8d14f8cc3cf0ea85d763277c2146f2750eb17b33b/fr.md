```
MenuMultiSélection
```

Un menu qui permet à un utilisateur de sélectionner plusieurs options dans une liste.

# Sortie d'exemple

```julia-repl
julia> request(MultiSelectMenu(options))
Sélectionnez les fruits que vous aimez :
[appuyez sur : Entrée=basculer, a=tous, n=aucun, d=terminé, q=abandonner]
   [ ] pomme
 > [X] orange
   [X] raisin
   [ ] fraise
   [ ] myrtille
   [X] pêche
   [ ] citron
   [ ] lime
Vous aimez les fruits suivants :
  - orange
  - raisin
  - pêche
```
