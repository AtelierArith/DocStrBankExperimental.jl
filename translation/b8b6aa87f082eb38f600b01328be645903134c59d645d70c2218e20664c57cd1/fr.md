```
while
```

Les boucles `while` évaluent de manière répétée une expression conditionnelle et continuent d'évaluer le corps de la boucle `while` tant que l'expression reste vraie. Si l'expression conditionnelle est fausse lorsque la boucle `while` est atteinte pour la première fois, le corps n'est jamais évalué.

# Exemples

```jldoctest
julia> i = 1
1

julia> while i < 5
           println(i)
           global i += 1
       end
1
2
3
4
```
