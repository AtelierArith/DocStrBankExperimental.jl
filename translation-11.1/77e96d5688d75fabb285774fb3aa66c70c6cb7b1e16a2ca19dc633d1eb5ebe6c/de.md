```
@async
```

Wickeln Sie einen Ausdruck in eine [`Task`](@ref) und fügen Sie ihn der Warteschlange des lokalen Maschinenplaners hinzu.

Werte können über `$` in `@async` interpoliert werden, was den Wert direkt in den konstruierten zugrunde liegenden Closure kopiert. Dies ermöglicht es Ihnen, den *Wert* einer Variablen einzufügen und den asynchronen Code von Änderungen des Wertes der Variablen in der aktuellen Aufgabe zu isolieren.

!!! warning
    Es wird dringend empfohlen, `Threads.@spawn` immer `@async` vorzuziehen, **auch wenn keine Parallelität erforderlich ist**, insbesondere in öffentlich verteilten Bibliotheken. Dies liegt daran, dass die Verwendung von `@async` die Migration der *Eltern*-Aufgabe über Arbeits-Threads in der aktuellen Implementierung von Julia deaktiviert. Daher kann die scheinbar harmlose Verwendung von `@async` in einer Bibliotheksfunktion erhebliche Auswirkungen auf die Leistung sehr unterschiedlicher Teile von Benutzeranwendungen haben.


!!! compat "Julia 1.4"
    Die Interpolation von Werten über `$` ist seit Julia 1.4 verfügbar.

