```
Base.identify_package(name::String)::Union{PkgId, Nothing}
Base.identify_package(where::Union{Module,PkgId}, name::String)::Union{PkgId, Nothing}
```

Identifica el paquete por su nombre desde la pila del entorno actual, devolviendo su `PkgId`, o `nothing` si no se puede encontrar.

Si solo se proporciona el argumento `name`, busca en cada entorno de la pila y sus dependencias directas nombradas.

El argumento `where` proporciona el contexto desde donde buscar el paquete: en este caso, primero verifica si el nombre coincide con el contexto mismo, de lo contrario, busca todas las dependencias recursivas (del manifiesto resuelto de cada entorno) hasta localizar el contexto `where`, y desde allí identifica la dependencia con el nombre correspondiente.

```julia-repl
julia> Base.identify_package("Pkg") # Pkg es una dependencia del entorno por defecto
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> using LinearAlgebra

julia> Base.identify_package(LinearAlgebra, "Pkg") # Pkg no es una dependencia de LinearAlgebra
```
