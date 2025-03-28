```
treewalk(f, tree::GitTree, post::Bool=false)
```

Durchlaufe die Einträge in `tree` und seinen Unterbäumen in post- oder pre-order. Preorder bedeutet, am Wurzelknoten zu beginnen und dann den linksseitigsten Unterbaum zu durchlaufen (und rekursiv weiter durch die linksseitigsten Unterbäume dieses Unterbaums) und sich nach rechts durch die Unterbäume zu bewegen. Postorder bedeutet, am Boden des linksseitigsten Unterbaums zu beginnen, durch ihn nach oben zu traversieren, dann den nächsten rechten Unterbaum zu durchlaufen (wiederum beginnend am Boden) und schließlich den Wurzelknoten des Baumes zuletzt zu besuchen.

Der Funktionsparameter `f` sollte folgende Signatur haben:

```
(String, GitTreeEntry) -> Cint
```

Ein negativer Wert, der von `f` zurückgegeben wird, stoppt den Baumdurchlauf. Ein positiver Wert bedeutet, dass der Eintrag übersprungen wird, wenn `post` `false` ist.
