```
var
```

La syntaxe `var"#example#"` fait référence à une variable nommée `Symbol("#example#")`, même si `#example#` n'est pas un nom d'identifiant valide en Julia.

Cela peut être utile pour l'interopérabilité avec des langages de programmation qui ont des règles différentes pour la construction d'identifiants valides. Par exemple, pour faire référence à la variable `R` `draw.segments`, vous pouvez utiliser `var"draw.segments"` dans votre code Julia.

Il est également utilisé pour `show` le code source julia qui a été soumis à l'hygiène des macros ou qui contient autrement des noms de variables qui ne peuvent pas être analysés normalement.

Notez que cette syntaxe nécessite un support du parseur, elle est donc étendue directement par le parseur plutôt que d'être implémentée comme une macro de chaîne normale `@var_str`.

!!! compat "Julia 1.3"
    Cette syntaxe nécessite au moins Julia 1.3.

