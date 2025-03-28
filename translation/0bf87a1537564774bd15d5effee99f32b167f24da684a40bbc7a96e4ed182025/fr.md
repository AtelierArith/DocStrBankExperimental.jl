```
localindices(S::SharedArray)
```

Renvoie une plage décrivant les "indices par défaut" à traiter par le processus actuel. Cette plage doit être interprétée dans le sens de l'indexation linéaire, c'est-à-dire comme une sous-plage de `1:length(S)`. Dans des contextes multi-processus, renvoie une plage vide dans le processus parent (ou tout processus pour lequel [`indexpids`](@ref) renvoie 0).

Il convient de souligner que `localindices` existe uniquement par commodité, et vous pouvez partitionner le travail sur le tableau parmi les travailleurs comme vous le souhaitez. Pour un `SharedArray`, tous les indices devraient être également rapides pour chaque processus de travail.
