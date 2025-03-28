```
getglobal(module::Module, name::Symbol, [order::Symbol=:monotonic])
```

Ruft den Wert der Bindung `name` aus dem Modul `module` ab. Optional kann eine atomare Reihenfolge für den Vorgang definiert werden, andernfalls wird standardmäßig monotonic verwendet.

Obwohl der Zugriff auf Modulbindungen mit [`getfield`](@ref) weiterhin unterstützt wird, um die Kompatibilität aufrechtzuerhalten, sollte immer `getglobal` bevorzugt werden, da `getglobal` die Kontrolle über die atomare Reihenfolge ermöglicht (`getfield` ist immer monotonic) und die Absicht des Codes sowohl für den Benutzer als auch für den Compiler besser signalisiert.

Die meisten Benutzer sollten diese Funktion nicht direkt aufrufen müssen – Die Funktion [`getproperty`](@ref Base.getproperty) oder die entsprechende Syntax (d.h. `module.name`) sollte in allen, bis auf sehr wenigen spezifischen Anwendungsfällen, bevorzugt werden.

!!! compat "Julia 1.9"
    Diese Funktion erfordert Julia 1.9 oder höher.


Siehe auch [`getproperty`](@ref Base.getproperty) und [`setglobal!`](@ref).

# Beispiele

```jldoctest
julia> a = 1
1

julia> module M
       a = 2
       end;

julia> getglobal(@__MODULE__, :a)
1

julia> getglobal(M, :a)
2
```
