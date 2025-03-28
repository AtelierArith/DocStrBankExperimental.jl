```
return
```

`return x` fait sortir la fonction englobante plus tôt, en renvoyant la valeur donnée `x` à son appelant. `return` tout seul sans valeur est équivalent à `return nothing` (voir [`nothing`](@ref)).

```julia
function compare(a, b)
    a == b && return "égal à"
    a < b ? "moins que" : "plus que"
end
```

En général, vous pouvez placer une instruction `return` n'importe où dans le corps d'une fonction, y compris dans des boucles ou des conditionnelles profondément imbriquées, mais faites attention avec les blocs `do`. Par exemple :

```julia
function test1(xs)
    for x in xs
        iseven(x) && return 2x
    end
end

function test2(xs)
    map(xs) do x
        iseven(x) && return 2x
        x
    end
end
```

Dans le premier exemple, le retour sort de `test1` dès qu'il rencontre un nombre pair, donc `test1([5,6,7])` renvoie `12`.

Vous pourriez vous attendre à ce que le deuxième exemple se comporte de la même manière, mais en fait le `return` là ne sort que de la *fonction interne* (à l'intérieur du bloc `do`) et renvoie une valeur à `map`. `test2([5,6,7])` renvoie alors `[5,12,7]`.

Lorsqu'il est utilisé dans une expression de niveau supérieur (c'est-à-dire en dehors de toute fonction), `return` fait que l'ensemble de l'expression de niveau supérieur actuelle se termine plus tôt.
