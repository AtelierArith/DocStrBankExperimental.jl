```
setglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Setzen oder Ändern des Wertes der Bindung `name` im Modul `module` auf `x`. Es erfolgt keine Typumwandlung, sodass, wenn für die Bindung bereits ein Typ deklariert wurde, `x` vom entsprechenden Typ sein muss, oder es wird ein Fehler ausgelöst.

Zusätzlich kann eine atomare Reihenfolge für diesen Vorgang angegeben werden, andernfalls wird standardmäßig monotonic verwendet.

Benutzer greifen typischerweise über die Funktion [`setproperty!`](@ref Base.setproperty!) oder die entsprechende Syntax (d.h. `module.name = x`) auf diese Funktionalität zu, daher ist dies nur für sehr spezifische Anwendungsfälle gedacht.

!!! compat "Julia 1.9"
    Diese Funktion erfordert Julia 1.9 oder höher.


Siehe auch [`setproperty!`](@ref Base.setproperty!) und [`getglobal`](@ref)

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> module M; global a; end;

julia> M.a  # dasselbe wie `getglobal(M, :a)`
ERROR: UndefVarError: `a` nicht in `M` definiert
Vorschlag: Fügen Sie einen entsprechenden Import oder eine Zuweisung hinzu. Diese globale Variable wurde deklariert, aber nicht zugewiesen.
Stacktrace:
 [1] getproperty(x::Module, f::Symbol)
   @ Base ./Base.jl:42
 [2] oberste Ebene
   @ none:1

julia> setglobal!(M, :a, 1)
1

julia> M.a
1
```
