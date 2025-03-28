# Documentation

Les fonctions, méthodes et types peuvent être documentés en plaçant une chaîne de caractères avant la définition :

```
"""
# La fonction Foo
`foo(x)`: Foo le diable vivant hors de `x`.
"""
foo(x) = ...
```

Le macro `@doc` peut être utilisé directement pour définir et récupérer la documentation / les métadonnées. Le macro a un parsing spécial afin que l'objet documenté puisse apparaître sur la ligne suivante :

```
@doc "blah"
function foo() ...
```

Par défaut, la documentation est écrite en Markdown, mais tout objet peut être utilisé comme premier argument.

## Documenter des objets séparément de leurs définitions

Vous pouvez documenter un objet avant ou après sa définition avec

```
@doc "foo" function_to_doc
@doc "bar" TypeToDoc
```

Pour les macros, la syntaxe est `@doc "macro doc" :(Module.@macro)` ou `@doc "macro doc" :(string_macro"")` pour les macros de chaîne. Sans les guillemets `:()`, l'expansion de la macro sera documentée.

## Récupérer la documentation

Vous pouvez récupérer la documentation pour les fonctions, macros et autres objets comme suit :

```
@doc foo
@doc @time
@doc md""
```

## Fonctions & Méthodes

Placer la documentation avant une définition de méthode (par exemple `function foo() ...` ou `foo() = ...`) fera en sorte que cette méthode spécifique soit documentée, par opposition à la fonction entière. Les docs des méthodes sont concaténées dans l'ordre où elles ont été définies pour fournir des docs pour la fonction.
