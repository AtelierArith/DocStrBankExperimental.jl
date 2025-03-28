```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Führen Sie eine Vergleich-und-Tausch-Operation auf `x.f` von `expected` zu `desired` durch, gemäß egal. Die Syntax `@atomicreplace x.f expected => desired` kann anstelle der Funktionsaufrufsform verwendet werden.

Siehe auch [`replacefield!`](@ref Core.replacefield!) [`setproperty!`](@ref Base.setproperty!), [`setpropertyonce!`](@ref Base.setpropertyonce!).
