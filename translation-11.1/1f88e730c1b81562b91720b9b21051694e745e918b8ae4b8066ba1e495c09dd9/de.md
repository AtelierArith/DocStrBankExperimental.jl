```
setpropertyonce!(x, f::Symbol, value, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Führen Sie eine Vergleich-und-Tausch-Operation auf `x.f` durch, um es auf `value` zu setzen, wenn es zuvor nicht gesetzt war. Die Syntax `@atomiconce x.f = value` kann anstelle der Funktionsaufrufsform verwendet werden.

Siehe auch [`setfieldonce!`](@ref Core.replacefield!), [`setproperty!`](@ref Base.setproperty!), [`replaceproperty!`](@ref Base.replaceproperty!).

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.

