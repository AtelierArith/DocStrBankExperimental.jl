```
@r_str -> Regex
```

Construisez une regex, telle que `r"^[a-z]*$"`, sans interpolation et sans déséchapper (sauf pour le guillemet `"` qui doit toujours être échappé). La regex accepte également un ou plusieurs indicateurs, listés après la citation de fin, pour modifier son comportement :

  * `i` active la correspondance insensible à la casse
  * `m` traite les tokens `^` et `$` comme correspondant au début et à la fin de lignes individuelles, plutôt qu'à l'ensemble de la chaîne.
  * `s` permet au modificateur `.` de correspondre aux nouvelles lignes.
  * `x` active le "mode d'espacement libre" : les espaces entre les tokens regex sont ignorés sauf s'ils sont échappés avec `\`, et `#` dans la regex est traité comme le début d'un commentaire (qui est ignoré jusqu'à la fin de la ligne).
  * `a` active le mode ASCII (désactive les modes `UTF` et `UCP`). Par défaut, `\B`, `\b`, `\D`, `\d`, `\S`, `\s`, `\W`, `\w`, etc. correspondent en fonction des propriétés de caractères Unicode. Avec cette option, ces séquences ne correspondent qu'aux caractères ASCII. Cela inclut également `\u`, qui émettra la valeur de caractère spécifiée directement en tant que byte unique, et ne tentera pas de l'encoder en UTF-8. Il est important de noter que cette option permet de correspondre à des chaînes UTF-8 invalides, en traitant à la fois le matcher et la cible comme de simples bytes (comme s'ils étaient des bytes ISO/IEC 8859-1 / Latin-1) plutôt que comme des encodages de caractères. Dans ce cas, cette option est souvent combinée avec `s`. Cette option peut être affinée en commençant le motif par (*UCP) ou (*UTF).

Voir [`Regex`](@ref) si une interpolation est nécessaire.

# Exemples

```jldoctest
julia> match(r"a+.*b+.*?d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

Cette regex a les trois premiers indicateurs activés.
