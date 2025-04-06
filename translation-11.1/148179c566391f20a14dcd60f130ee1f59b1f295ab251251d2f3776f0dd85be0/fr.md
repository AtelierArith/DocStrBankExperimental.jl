```
Printf.Format(format_str)
```

Créez un objet de format compatible avec printf de C qui peut être utilisé pour formater des valeurs.

La chaîne d'entrée `format_str` peut inclure n'importe quel caractère de spécificateur de format valide et des modificateurs.

Un objet `Format` peut être passé à `Printf.format(f::Format, args...)` pour produire une chaîne formatée, ou `Printf.format(io::IO, f::Format, args...)` pour imprimer directement la chaîne formatée dans `io`.

Pour plus de commodité, la forme de macro de chaîne `Printf.format"..."` peut être utilisée pour construire un objet `Printf.Format` au moment de l'expansion de la macro.

!!! compat "Julia 1.6"
    `Printf.Format` nécessite Julia 1.6 ou une version ultérieure.

