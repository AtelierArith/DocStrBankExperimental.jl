```
parse(str; raise=true, depwarn=true, filename="none")
```

Analyse la chaîne d'expression de manière gourmande, renvoyant une seule expression. Une erreur est levée s'il y a des caractères supplémentaires après la première expression. Si `raise` est `true` (par défaut), les erreurs de syntaxe lèveront une erreur ; sinon, `parse` renverra une expression qui lèvera une erreur lors de l'évaluation. Si `depwarn` est `false`, les avertissements de dépréciation seront supprimés. L'argument `filename` est utilisé pour afficher des diagnostics lorsqu'une erreur est levée.

```jldoctest; filter=r"(?<=Expr\(:error).*|(?<=Expr\(:incomplete).*"
julia> Meta.parse("x = 3")
:(x = 3)

julia> Meta.parse("1.0.2")
ERROR: ParseError:
# Error @ none:1:1
1.0.2
└──┘ ── constante numérique invalide
[...]

julia> Meta.parse("1.0.2"; raise = false)
:($(Expr(:error, "constante numérique invalide "1.0."")))

julia> Meta.parse("x = ")
:($(Expr(:incomplete, "incomplet : fin prématurée de l'entrée")))
```
