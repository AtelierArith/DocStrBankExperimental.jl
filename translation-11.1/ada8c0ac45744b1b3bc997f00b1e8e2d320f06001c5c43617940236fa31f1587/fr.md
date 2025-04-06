```
@assert cond [texte]
```

Lance une [`AssertionError`](@ref) si `cond` est `false`. C'est la syntaxe préférée pour écrire des assertions, qui sont des conditions supposées vraies, mais que l'utilisateur pourrait décider de vérifier de toute façon, comme aide au débogage en cas d'échec. Le message optionnel `texte` est affiché en cas d'échec de l'assertion.

!!! avertissement
    Une assertion peut être désactivée à certains niveaux d'optimisation. Les assertions ne doivent donc être utilisées qu'en tant qu'outil de débogage et ne doivent pas être utilisées pour la vérification d'authentification (par exemple, vérifier des mots de passe ou vérifier les limites des tableaux). Le code ne doit pas dépendre des effets secondaires de l'exécution de `cond` pour le bon comportement d'une fonction.


# Exemples

```jldoctest
julia> @assert iseven(3) "3 est un nombre impair !"
ERROR: AssertionError: 3 est un nombre impair !

julia> @assert isodd(3) "Qu'est-ce qu'un nombre pair ?"
```
