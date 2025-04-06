```
include_string([mapexpr::Function,] m::Module, code::AbstractString, filename::AbstractString="string")
```

Wie [`include`](@ref), außer dass der Code aus dem angegebenen String anstelle einer Datei gelesen wird.

Das optionale erste Argument `mapexpr` kann verwendet werden, um den eingeschlossenen Code vor der Auswertung zu transformieren: Für jeden geparsten Ausdruck `expr` in `code` wertet die Funktion `include_string` tatsächlich `mapexpr(expr)` aus. Wenn es weggelassen wird, wird `mapexpr` standardmäßig auf [`identity`](@ref) gesetzt.

!!! compat "Julia 1.5"
    Julia 1.5 ist erforderlich, um das Argument `mapexpr` zu übergeben.

