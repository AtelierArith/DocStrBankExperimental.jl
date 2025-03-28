```
const
```

`const` wird verwendet, um globale Variablen zu deklarieren, deren Werte sich nicht ändern werden. In fast allen Code (und insbesondere in leistungsempfindlichem Code) sollten globale Variablen auf diese Weise konstant deklariert werden.

```julia
const x = 5
```

Mehrere Variablen können innerhalb eines einzelnen `const` deklariert werden:

```julia
const y, z = 7, 11
```

Beachten Sie, dass `const` nur für eine `=`-Operation gilt, daher deklariert `const x = y = 1` `x` als konstant, aber nicht `y`. Andererseits deklariert `const x = const y = 1` sowohl `x` als auch `y` als konstant.

Beachten Sie, dass die "Konstanz" nicht in veränderliche Container hineinreicht; nur die Zuordnung zwischen einer Variablen und ihrem Wert ist konstant. Wenn `x` ein Array oder ein Dictionary (zum Beispiel) ist, können Sie dennoch Elemente ändern, hinzufügen oder entfernen.

In einigen Fällen gibt das Ändern des Wertes einer `const`-Variablen eine Warnung anstelle eines Fehlers aus. Dies kann jedoch unvorhersehbares Verhalten erzeugen oder den Zustand Ihres Programms beschädigen, und sollte daher vermieden werden. Diese Funktion ist nur für den Komfort während der interaktiven Nutzung gedacht.
