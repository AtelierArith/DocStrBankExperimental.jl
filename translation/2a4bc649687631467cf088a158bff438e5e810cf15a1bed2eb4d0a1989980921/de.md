```
VersionNumber
```

Versionsnummerntyp, der den Spezifikationen von [semantischer Versionierung (semver)](https://semver.org/) folgt, bestehend aus Haupt-, Neben- und Patch-Zahlen, gefolgt von Vorab- und Build-alphanumerischen Anmerkungen.

`VersionNumber`-Objekte können mit allen Standardvergleichsoperatoren (`==`, `<`, `<=` usw.) verglichen werden, wobei das Ergebnis den semver-Regeln folgt.

`VersionNumber` hat die folgenden öffentlichen Felder:

  * `v.major::Integer`
  * `v.minor::Integer`
  * `v.patch::Integer`
  * `v.prerelease::Tuple{Vararg{Union{Integer, AbstractString}}}`
  * `v.build::Tuple{Vararg{Union{Integer, AbstractString}}}`

Siehe auch [`@v_str`](@ref), um `VersionNumber`-Objekte effizient aus semver-formatierten Literalzeichenfolgen zu erstellen, [`VERSION`](@ref) für die `VersionNumber` von Julia selbst und [Versionsnummern-Literale](@ref man-version-number-literals) im Handbuch.

# Beispiele

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
