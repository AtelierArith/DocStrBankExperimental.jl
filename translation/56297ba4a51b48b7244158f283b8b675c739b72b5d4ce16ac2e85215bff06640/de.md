```
Base.@constprop Einstellung [ex]
```

Steuern Sie den Modus der interprozeduralen konstanten Propagation für die annotierte Funktion.

Zwei `Einstellungen` werden unterstützt:

  * `Base.@constprop :aggressive [ex]`: wendet die konstante Propagation aggressiv an. Für eine Methode, bei der der Rückgabewert vom Wert der Argumente abhängt, kann dies verbesserte Inferenzresultate auf Kosten zusätzlicher Kompilierzeit liefern.
  * `Base.@constprop :none [ex]`: deaktiviert die konstante Propagation. Dies kann die Kompilierzeiten für Funktionen reduzieren, die Julia andernfalls für konstanten Propagation als wertvoll erachten könnte. Häufige Fälle sind Funktionen mit `Bool`- oder `Symbol`-wertigen Argumenten oder Schlüsselwortargumenten.

`Base.@constprop` kann unmittelbar vor einer Funktionsdefinition oder innerhalb eines Funktionskörpers angewendet werden.

```julia
# annotiere Langformdefinition
Base.@constprop :aggressive function longdef(x)
    ...
end

# annotiere Kurzformdefinition
Base.@constprop :aggressive shortdef(x) = ...

# annotiere anonyme Funktion, die ein `do`-Block erstellt
f() do
    Base.@constprop :aggressive
    ...
end
```

!!! compat "Julia 1.10"
    Die Verwendung innerhalb eines Funktionskörpers erfordert mindestens Julia 1.10.

