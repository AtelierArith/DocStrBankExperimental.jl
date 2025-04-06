```
styled(content::AbstractString) -> AnnotatedString
```

Construit une chaîne stylée. Dans la chaîne, les structures `{<specs>:<content>}` appliquent le formatage à `<content>`, selon la liste des spécifications séparées par des virgules `<specs>`. Chaque spécification peut prendre la forme d'un nom de police, d'une spécification de police en ligne, ou d'une paire `key=value`. La valeur doit être entourée par `{...}` si elle contient l'un des caractères `,=:{}`.

Ceci est un équivalent fonctionnel du macro [`@styled_str`](@ref), juste sans capacités d'interpolation.
