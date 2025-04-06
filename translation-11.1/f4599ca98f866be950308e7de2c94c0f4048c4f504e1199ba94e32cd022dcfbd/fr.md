```
asyncmap(f, c...; ntasks=0, batch_size=nothing)
```

Utilise plusieurs tâches concurrentes pour appliquer `f` sur une collection (ou plusieurs collections de même longueur). Pour plusieurs arguments de collection, `f` est appliqué élément par élément.

`ntasks` spécifie le nombre de tâches à exécuter de manière concurrente. En fonction de la longueur des collections, si `ntasks` n'est pas spécifié, jusqu'à 100 tâches seront utilisées pour le mappage concurrent.

`ntasks` peut également être spécifié comme une fonction sans argument. Dans ce cas, le nombre de tâches à exécuter en parallèle est vérifié avant le traitement de chaque élément et une nouvelle tâche est démarrée si la valeur de `ntasks_func` est supérieure au nombre actuel de tâches.

Si `batch_size` est spécifié, la collection est traitée en mode batch. `f` doit alors être une fonction qui doit accepter un `Vector` de tuples d'arguments et doit retourner un vecteur de résultats. Le vecteur d'entrée aura une longueur de `batch_size` ou moins.

Les exemples suivants mettent en évidence l'exécution dans différentes tâches en retournant l'`objectid` des tâches dans lesquelles la fonction de mappage est exécutée.

Tout d'abord, avec `ntasks` indéfini, chaque élément est traité dans une tâche différente.

```
julia> tskoid() = objectid(current_task());

julia> asyncmap(x->tskoid(), 1:5)
5-element Array{UInt64,1}:
 0x6e15e66c75c75853
 0x440f8819a1baa682
 0x9fb3eeadd0c83985
 0xebd3e35fe90d4050
 0x29efc93edce2b961

julia> length(unique(asyncmap(x->tskoid(), 1:5)))
5
```

Avec `ntasks=2`, tous les éléments sont traités dans 2 tâches.

```
julia> asyncmap(x->tskoid(), 1:5; ntasks=2)
5-element Array{UInt64,1}:
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94

julia> length(unique(asyncmap(x->tskoid(), 1:5; ntasks=2)))
2
```

Avec `batch_size` défini, la fonction de mappage doit être modifiée pour accepter un tableau de tuples d'arguments et retourner un tableau de résultats. `map` est utilisé dans la fonction de mappage modifiée pour y parvenir.

```
julia> batch_func(input) = map(x->string("args_tuple: ", x, ", element_val: ", x[1], ", task: ", tskoid()), input)
batch_func (generic function with 1 method)

julia> asyncmap(batch_func, 1:5; ntasks=2, batch_size=2)
5-element Array{String,1}:
 "args_tuple: (1,), element_val: 1, task: 9118321258196414413"
 "args_tuple: (2,), element_val: 2, task: 4904288162898683522"
 "args_tuple: (3,), element_val: 3, task: 9118321258196414413"
 "args_tuple: (4,), element_val: 4, task: 4904288162898683522"
 "args_tuple: (5,), element_val: 5, task: 9118321258196414413"
```
