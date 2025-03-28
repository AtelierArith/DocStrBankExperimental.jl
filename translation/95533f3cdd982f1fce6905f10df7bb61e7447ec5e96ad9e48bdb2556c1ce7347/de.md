```
rethrow()
```

Wirft die aktuelle Ausnahme innerhalb eines `catch`-Blocks erneut. Die erneut geworfene Ausnahme wird weiterhin propagiert, als ob sie nicht abgefangen worden wäre.

!!! Hinweis     Die alternative Form `rethrow(e)` ermöglicht es Ihnen, ein alternatives Ausnahmeobjekt `e` mit dem aktuellen Backtrace zu verknüpfen. Dies stellt jedoch den Programmzustand zum Zeitpunkt des Fehlers falsch dar, weshalb Sie stattdessen ermutigt werden, eine neue Ausnahme mit `throw(e)` zu werfen. In Julia 1.1 und höher wird durch die Verwendung von `throw(e)` die ursprüngliche Ausnahmeursache im Stack beibehalten, wie in [`current_exceptions`](@ref) beschrieben.
