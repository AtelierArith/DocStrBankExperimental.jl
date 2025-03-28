```
SharedArray{T}(dims::NTuple; init=false, pids=Int[])
SharedArray{T,N}(...)
```

Construit un `SharedArray` d'un type de bits `T` et de taille `dims` à travers les processus spécifiés par `pids` - tous devant être sur le même hôte. Si `N` est spécifié en appelant `SharedArray{T,N}(dims)`, alors `N` doit correspondre à la longueur de `dims`.

Si `pids` est laissé non spécifié, le tableau partagé sera mappé à travers tous les processus sur l'hôte actuel, y compris le maître. Cependant, `localindices` et `indexpids` ne feront référence qu'aux processus de travail. Cela facilite le code de distribution de travail pour utiliser des travailleurs pour le calcul réel avec le processus maître agissant comme un conducteur.

Si une fonction `init` de type `initfn(S::SharedArray)` est spécifiée, elle est appelée sur tous les travailleurs participants.

Le tableau partagé est valide tant qu'une référence à l'objet `SharedArray` existe sur le nœud qui a créé le mappage.

```
SharedArray{T}(filename::AbstractString, dims::NTuple, [offset=0]; mode=nothing, init=false, pids=Int[])
SharedArray{T,N}(...)
```

Construit un `SharedArray` soutenu par le fichier `filename`, avec un type d'élément `T` (doit être un type de bits) et de taille `dims`, à travers les processus spécifiés par `pids` - tous devant être sur le même hôte. Ce fichier est mappé dans la mémoire de l'hôte, avec les conséquences suivantes :

  * Les données du tableau doivent être représentées au format binaire (par exemple, un format ASCII comme CSV ne peut pas être pris en charge)
  * Toute modification que vous apportez aux valeurs du tableau (par exemple, `A[3] = 0`) changera également les valeurs sur le disque

Si `pids` est laissé non spécifié, le tableau partagé sera mappé à travers tous les processus sur l'hôte actuel, y compris le maître. Cependant, `localindices` et `indexpids` ne feront référence qu'aux processus de travail. Cela facilite le code de distribution de travail pour utiliser des travailleurs pour le calcul réel avec le processus maître agissant comme un conducteur.

`mode` doit être l'un de `"r"`, `"r+"`, `"w+"`, ou `"a+"`, et par défaut à `"r+"` si le fichier spécifié par `filename` existe déjà, ou `"w+"` sinon. Si une fonction `init` de type `initfn(S::SharedArray)` est spécifiée, elle est appelée sur tous les travailleurs participants. Vous ne pouvez pas spécifier de fonction `init` si le fichier n'est pas écrivable.

`offset` vous permet de sauter le nombre spécifié d'octets au début du fichier.
