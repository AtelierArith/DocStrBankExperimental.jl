```
parse(str, start; greedy=true, raise=true, depwarn=true, filename="none")
```

Analyse la chaîne d'expression et retourne une expression (qui pourrait ensuite être passée à eval pour exécution). `start` est l'index de l'unité de code dans `str` du premier caractère à partir duquel commencer l'analyse (comme pour tous les index de chaîne, ce ne sont pas des indices de caractères). Si `greedy` est `true` (par défaut), `parse` essaiera de consommer autant d'entrée qu'il le peut ; sinon, il s'arrêtera dès qu'il a analysé une expression valide. Les expressions incomplètes mais autrement syntaxiquement valides retourneront `Expr(:incomplete, "(message d'erreur)")`. Si `raise` est `true` (par défaut), les erreurs de syntaxe autres que les expressions incomplètes lèveront une erreur. Si `raise` est `false`, `parse` retournera une expression qui lèvera une erreur lors de l'évaluation. Si `depwarn` est `false`, les avertissements de dépréciation seront supprimés. L'argument `filename` est utilisé pour afficher des diagnostics lorsqu'une erreur est levée.

```jldoctest
julia> Meta.parse("(α, β) = 3, 5", 1) # début de la chaîne
(:((α, β) = (3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 1, greedy=false)
(:((α, β)), 9)

julia> Meta.parse("(α, β) = 3, 5", 16) # fin de la chaîne
(nothing, 16)

julia> Meta.parse("(α, β) = 3, 5", 11) # index de 3
(:((3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 11, greedy=false)
(3, 13)
```
