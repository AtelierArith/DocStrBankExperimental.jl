```
@fastmath expr
```

Führen Sie eine transformierte Version des Ausdrucks aus, die Funktionen aufruft, die die strengen IEEE-Semantiken verletzen können. Dies ermöglicht die schnellstmögliche Ausführung, aber die Ergebnisse sind undefiniert – seien Sie vorsichtig, wenn Sie dies tun, da es die numerischen Ergebnisse ändern kann.

Dies setzt die [LLVM Fast-Math-Flags](https://llvm.org/docs/LangRef.html#fast-math-flags) und entspricht der Option `-ffast-math` in clang. Siehe [die Hinweise zu Leistungsannotationen](@ref man-performance-annotations) für weitere Details.

# Beispiele

```jldoctest
julia> @fastmath 1+2
3

julia> @fastmath(sin(3))
0.1411200080598672
```
