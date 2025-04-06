```
public
```

`public` wird innerhalb von Modulen verwendet, um Julia mitzuteilen, welche Namen Teil der öffentlichen API des Moduls sind. Zum Beispiel: `public foo` zeigt an, dass der Name `foo` öffentlich ist, ohne ihn verfügbar zu machen, wenn [`using`](@ref) das Modul verwendet wird. Siehe den [Handbuchabschnitt über Module](@ref modules) für Details.

!!! compat "Julia 1.11"
    Das Schlüsselwort public wurde in Julia 1.11 hinzugefügt. Davor war das Konzept der Öffentlichkeit weniger explizit.

