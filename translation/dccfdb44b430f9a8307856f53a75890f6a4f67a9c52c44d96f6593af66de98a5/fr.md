```
ImmutableDict
```

`ImmutableDict` est un dictionnaire implémenté comme une liste chaînée immuable, qui est optimal pour les petits dictionnaires construits à partir de nombreuses insertions individuelles. Notez qu'il n'est pas possible de supprimer une valeur, bien qu'elle puisse être partiellement remplacée et cachée en insérant une nouvelle valeur avec la même clé.

```
ImmutableDict(KV::Pair)
```

Créez une nouvelle entrée dans le `ImmutableDict` pour une paire `clé => valeur`

  * utilisez `(clé => valeur) in dict` pour voir si cette combinaison particulière est dans l'ensemble des propriétés
  * utilisez `get(dict, clé, défaut)` pour récupérer la valeur la plus récente pour une clé particulière
