```
Funktion
```

Funktionen werden mit dem Schlüsselwort `function` definiert:

```julia
function add(a, b)
    return a + b
end
```

Oder in der Kurzform:

```julia
add(a, b) = a + b
```

Die Verwendung des [`return`](@ref) Schlüsselworts ist genau die gleiche wie in anderen Sprachen, ist aber oft optional. Eine Funktion ohne eine explizite `return`-Anweisung gibt den letzten Ausdruck im Funktionskörper zurück.
