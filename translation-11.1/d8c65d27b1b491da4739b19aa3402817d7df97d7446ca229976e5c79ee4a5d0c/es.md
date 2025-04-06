# Module loading

[`Base.require`](@ref) es responsable de cargar módulos y también gestiona la caché de precompilación. Es la implementación de la declaración `import`.

## Experimental features

Las características a continuación son experimentales y no forman parte de la API estable de Julia. Antes de basarte en ellas, infórmate sobre el pensamiento actual y si podrían cambiar pronto.

### Package loading callbacks

Es posible escuchar los paquetes cargados por `Base.require`, registrando un callback.

```julia
loaded_packages = Base.PkgId[]
callback = (pkg::Base.PkgId) -> push!(loaded_packages, pkg)
push!(Base.package_callbacks, callback)
```

Usar esto se vería algo así:

```julia-repl
julia> using Example

julia> loaded_packages
1-element Vector{Base.PkgId}:
 Example [7876af07-990d-54b4-ab0e-23690620f79a]
```
