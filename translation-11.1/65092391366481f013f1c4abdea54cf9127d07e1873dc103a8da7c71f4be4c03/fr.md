```
Symbole
```

Le type d'objet utilisé pour représenter des identifiants dans le code julia analysé (ASTs). Utilisé également souvent comme un nom ou une étiquette pour identifier une entité (par exemple, comme clé de dictionnaire). Les `Symbol`s peuvent être saisis en utilisant l'opérateur de citation `:` :

```jldoctest
julia> :name
:name

julia> typeof(:name)
Symbol

julia> x = 42
42

julia> eval(:x)
42
```

Les `Symbol`s peuvent également être construits à partir de chaînes de caractères ou d'autres valeurs en appelant le constructeur `Symbol(x...)`.

Les `Symbol`s sont immuables et leur implémentation réutilise le même objet pour tous les `Symbol`s ayant le même nom.

Contrairement aux chaînes de caractères, les `Symbol`s sont des entités "atomiques" ou "scalaires" qui ne prennent pas en charge l'itération sur les caractères.
