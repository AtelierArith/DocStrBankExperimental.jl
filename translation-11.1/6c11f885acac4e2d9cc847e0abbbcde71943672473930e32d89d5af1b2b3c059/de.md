```
upstream(ref::GitReference) -> Union{GitReference, Nothing}
```

Bestimmen Sie, ob der Branch, der `ref` enthält, einen bestimmten Upstream-Branch hat.

Geben Sie entweder eine `GitReference` auf den Upstream-Branch zurück, wenn er existiert, oder [`nothing`](@ref), wenn der angeforderte Branch keinen Upstream-Gegenpart hat.
