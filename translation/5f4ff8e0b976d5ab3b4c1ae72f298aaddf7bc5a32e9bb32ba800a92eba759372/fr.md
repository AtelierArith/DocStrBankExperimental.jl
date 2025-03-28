```
using
```

`using Foo` chargera le module ou le paquet `Foo` et rendra ses noms [`export`](@ref)és disponibles pour une utilisation directe. Les noms peuvent également être utilisés via la syntaxe par point (par exemple `Foo.foo` pour accéder au nom `foo`), qu'ils soient `export`és ou non. Voir la [section du manuel sur les modules](@ref modules) pour plus de détails.

!!! note
    Lorsque deux ou plusieurs paquets/modules exportent un nom et que ce nom ne fait pas référence à la même chose dans chacun des paquets, et que les paquets sont chargés via `using` sans une liste explicite de noms, il est alors erroné de référencer ce nom sans qualification. Il est donc recommandé que le code destiné à être compatible avec les futures versions de ses dépendances et de Julia, par exemple, le code dans les paquets publiés, liste les noms qu'il utilise de chaque paquet chargé, par exemple `using Foo: Foo, f` plutôt que `using Foo`.

