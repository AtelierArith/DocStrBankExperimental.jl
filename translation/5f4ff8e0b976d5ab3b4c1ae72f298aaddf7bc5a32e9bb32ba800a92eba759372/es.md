```
using
```

`using Foo` cargará el módulo o paquete `Foo` y hará que sus nombres [`export`](@ref)ados estén disponibles para su uso directo. Los nombres también se pueden usar a través de la sintaxis de punto (por ejemplo, `Foo.foo` para acceder al nombre `foo`), ya sea que estén `export`ados o no. Consulta la [sección del manual sobre módulos](@ref modules) para más detalles.

!!! note
    Cuando dos o más paquetes/módulos exportan un nombre y ese nombre no se refiere a lo mismo en cada uno de los paquetes, y los paquetes se cargan a través de `using` sin una lista explícita de nombres, es un error hacer referencia a ese nombre sin calificación. Por lo tanto, se recomienda que el código destinado a ser compatible con versiones futuras de sus dependencias y de Julia, por ejemplo, el código en paquetes liberados, liste los nombres que utiliza de cada paquete cargado, por ejemplo, `using Foo: Foo, f` en lugar de `using Foo`.

