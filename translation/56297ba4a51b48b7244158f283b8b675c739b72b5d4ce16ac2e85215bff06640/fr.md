```
Base.@constprop réglage [ex]
```

Contrôlez le mode de propagation constante interprocédurale pour la fonction annotée.

Deux `réglages` sont pris en charge :

  * `Base.@constprop :aggressive [ex]` : appliquez la propagation constante de manière agressive. Pour une méthode dont le type de retour dépend de la valeur des arguments, cela peut donner de meilleurs résultats d'inférence au prix d'un temps de compilation supplémentaire.
  * `Base.@constprop :none [ex]` : désactivez la propagation constante. Cela peut réduire les temps de compilation pour les fonctions que Julia pourrait autrement juger dignes de propagation constante. Les cas courants concernent les fonctions avec des arguments de type `Bool` ou `Symbol` ou des arguments de mot-clé.

`Base.@constprop` peut être appliqué immédiatement avant une définition de fonction ou dans le corps d'une fonction.

```julia
# annoter une définition longue
Base.@constprop :aggressive function longdef(x)
    ...
end

# annoter une définition courte
Base.@constprop :aggressive shortdef(x) = ...

# annoter une fonction anonyme qu'un bloc `do` crée
f() do
    Base.@constprop :aggressive
    ...
end
```

!!! compat "Julia 1.10"
    L'utilisation dans le corps d'une fonction nécessite au moins Julia 1.10.

