```
promote_type(type1, type2, ...)
```

Die Promotion bezieht sich auf die Umwandlung von Werten gemischter Typen in einen einzigen gemeinsamen Typ. `promote_type` stellt das Standard-Promotionsverhalten in Julia dar, wenn Operatoren (in der Regel mathematische) Argumente unterschiedlicher Typen erhalten. `promote_type` versucht im Allgemeinen, einen Typ zurückzugeben, der zumindest die meisten Werte eines der Eingabetypen ohne übermäßige Erweiterung annähern kann. Ein gewisser Verlust wird toleriert; zum Beispiel gibt `promote_type(Int64, Float64)` [`Float64`](@ref) zurück, obwohl streng genommen nicht alle [`Int64`](@ref)-Werte genau als `Float64`-Werte dargestellt werden können.

Siehe auch: [`promote`](@ref), [`promote_typejoin`](@ref), [`promote_rule`](@ref).

# Beispiele

```jldoctest
julia> promote_type(Int64, Float64)
Float64

julia> promote_type(Int32, Int64)
Int64

julia> promote_type(Float32, BigInt)
BigFloat

julia> promote_type(Int16, Float16)
Float16

julia> promote_type(Int64, Float16)
Float16

julia> promote_type(Int8, UInt16)
UInt16
```

!!! warning "Überladen Sie dies nicht direkt"
    Um die Promotion für Ihre eigenen Typen zu überladen, sollten Sie [`promote_rule`](@ref) überladen. `promote_type` ruft intern `promote_rule` auf, um den Typ zu bestimmen. Das direkte Überladen von `promote_type` kann zu Mehrdeutigkeitsfehlern führen.


```
