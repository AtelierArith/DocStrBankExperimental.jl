```
module
```

`module` déclare un [`Module`](@ref), qui est un espace de travail de variables globales séparé. Dans un module, vous pouvez contrôler quels noms d'autres modules sont visibles (via l'importation) et spécifier lesquels de vos noms sont destinés à être publics (via `export` et `public`). Les modules vous permettent de créer des définitions de niveau supérieur sans vous soucier des conflits de noms lorsque votre code est utilisé avec celui de quelqu'un d'autre. Voir la [section du manuel sur les modules](@ref modules) pour plus de détails.

# Exemples

```julia
module Foo
import Base.show
export MyType, foo

struct MyType
    x
end

bar(x) = 2x
foo(a::MyType) = bar(a.x) + 1
show(io::IO, a::MyType) = print(io, "MyType $(a.x)")
end
```
