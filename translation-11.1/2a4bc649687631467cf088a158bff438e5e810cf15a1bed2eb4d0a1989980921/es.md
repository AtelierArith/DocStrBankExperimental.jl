```
VersionNumber
```

Tipo de número de versión que sigue las especificaciones de [versionado semántico (semver)](https://semver.org/), compuesto por valores numéricos mayor, menor y de parche, seguidos de anotaciones alfanuméricas de pre-lanzamiento y construcción.

Los objetos `VersionNumber` se pueden comparar con todos los operadores de comparación estándar (`==`, `<`, `<=`, etc.), con el resultado siguiendo las reglas de semver.

`VersionNumber` tiene los siguientes campos públicos:

  * `v.major::Integer`
  * `v.minor::Integer`
  * `v.patch::Integer`
  * `v.prerelease::Tuple{Vararg{Union{Integer, AbstractString}}}`
  * `v.build::Tuple{Vararg{Union{Integer, AbstractString}}}`

Véase también [`@v_str`](@ref) para construir de manera eficiente objetos `VersionNumber` a partir de cadenas literales en formato semver, [`VERSION`](@ref) para el `VersionNumber` de Julia en sí, y [Literales de Números de Versión](@ref man-version-number-literals) en el manual.

# Ejemplos

```jldoctest
julia> a = VersionNumber(1, 2, 3)
v"1.2.3"

julia> a >= v"1.2"
true

julia> b = VersionNumber("2.0.1-rc1")
v"2.0.1-rc1"

julia> b >= v"2.0.1"
false
```
