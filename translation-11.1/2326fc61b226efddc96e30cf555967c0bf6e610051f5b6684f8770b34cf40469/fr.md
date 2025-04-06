```
asyncmap!(f, results, c...; ntasks=0, batch_size=nothing)
```

Comme [`asyncmap`](@ref), mais stocke la sortie dans `results` plutôt que de renvoyer une collection.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

