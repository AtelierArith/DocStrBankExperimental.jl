```
if/elseif/else
```

`if`/`elseif`/`else` effectue une évaluation conditionnelle, ce qui permet à des portions de code d'être évaluées ou non en fonction de la valeur d'une expression booléenne. Voici l'anatomie de la syntaxe conditionnelle `if`/`elseif`/`else` :

```julia
if x < y
    println("x est inférieur à y")
elseif x > y
    println("x est supérieur à y")
else
    println("x est égal à y")
end
```

Si l'expression conditionnelle `x < y` est vraie, alors le bloc correspondant est évalué ; sinon, l'expression conditionnelle `x > y` est évaluée, et si elle est vraie, le bloc correspondant est évalué ; si aucune des deux expressions n'est vraie, le bloc `else` est évalué. Les blocs `elseif` et `else` sont optionnels, et autant de blocs `elseif` que désiré peuvent être utilisés.

Contrairement à certains autres langages, les conditions doivent être de type `Bool`. Il ne suffit pas que les conditions soient convertibles en `Bool`.

```jldoctest
julia> if 1 end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```
