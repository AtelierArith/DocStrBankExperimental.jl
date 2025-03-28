# Module loading

[`Base.require`](@ref) ist verantwortlich für das Laden von Modulen und verwaltet auch den Precompilation-Cache. Es ist die Implementierung der `import`-Anweisung.

## Experimental features

Die untenstehenden Funktionen sind experimentell und nicht Teil der stabilen Julia-API. Informieren Sie sich, bevor Sie darauf aufbauen, über die aktuelle Denkweise und ob sie sich bald ändern könnten.

### Package loading callbacks

Es ist möglich, die von `Base.require` geladenen Pakete anzuhören, indem man einen Callback registriert.

```julia
loaded_packages = Base.PkgId[]
callback = (pkg::Base.PkgId) -> push!(loaded_packages, pkg)
push!(Base.package_callbacks, callback)
```

Die Verwendung davon würde etwa so aussehen:

```julia-repl
julia> using Example

julia> loaded_packages
1-element Vector{Base.PkgId}:
 Example [7876af07-990d-54b4-ab0e-23690620f79a]
```
