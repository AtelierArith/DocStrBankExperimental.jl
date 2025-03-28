```
readdir(dir::AbstractString=pwd();
    join::Bool = false,
    sort::Bool = true,
) -> Vector{String}
```

Devuelve los nombres en el directorio `dir` o el directorio de trabajo actual si no se proporciona. Cuando `join` es falso, `readdir` devuelve solo los nombres en el directorio tal como están; cuando `join` es verdadero, devuelve `joinpath(dir, name)` para cada `name` de modo que las cadenas devueltas sean rutas completas. Si deseas obtener rutas absolutas, llama a `readdir` con una ruta de directorio absoluta y `join` configurado en verdadero.

Por defecto, `readdir` ordena la lista de nombres que devuelve. Si deseas omitir el ordenamiento de los nombres y obtenerlos en el orden en que el sistema de archivos los lista, puedes usar `readdir(dir, sort=false)` para optar por no ordenar.

Ver también: [`walkdir`](@ref).

!!! compat "Julia 1.4"
    Los argumentos de palabra clave `join` y `sort` requieren al menos Julia 1.4.


# Ejemplos

```julia-repl
julia> cd("/home/JuliaUser/dev/julia")

julia> readdir()
30-element Array{String,1}:
 ".appveyor.yml"
 ".git"
 ".gitattributes"
 ⋮
 "ui"
 "usr"
 "usr-staging"

julia> readdir(join=true)
30-element Array{String,1}:
 "/home/JuliaUser/dev/julia/.appveyor.yml"
 "/home/JuliaUser/dev/julia/.git"
 "/home/JuliaUser/dev/julia/.gitattributes"
 ⋮
 "/home/JuliaUser/dev/julia/ui"
 "/home/JuliaUser/dev/julia/usr"
 "/home/JuliaUser/dev/julia/usr-staging"

julia> readdir("base")
145-element Array{String,1}:
 ".gitignore"
 "Base.jl"
 "Enums.jl"
 ⋮
 "version_git.sh"
 "views.jl"
 "weakkeydict.jl"

julia> readdir("base", join=true)
145-element Array{String,1}:
 "base/.gitignore"
 "base/Base.jl"
 "base/Enums.jl"
 ⋮
 "base/version_git.sh"
 "base/views.jl"
 "base/weakkeydict.jl"

julia> readdir(abspath("base"), join=true)
145-element Array{String,1}:
 "/home/JuliaUser/dev/julia/base/.gitignore"
 "/home/JuliaUser/dev/julia/base/Base.jl"
 "/home/JuliaUser/dev/julia/base/Enums.jl"
 ⋮
 "/home/JuliaUser/dev/julia/base/version_git.sh"
 "/home/JuliaUser/dev/julia/base/views.jl"
 "/home/JuliaUser/dev/julia/base/weakkeydict.jl"
```
