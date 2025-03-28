```
@simd
```

Annotieren Sie eine `for`-Schleife, um dem Compiler zusätzliche Freiheiten zu ermöglichen, um die Schleifenreihenfolge zu ändern.

!!! warning
    Diese Funktion ist experimentell und könnte sich in zukünftigen Versionen von Julia ändern oder verschwinden. Falsche Verwendung des `@simd`-Makros kann unerwartete Ergebnisse verursachen.


Das Objekt, über das in einer `@simd for`-Schleife iteriert wird, sollte ein eindimensionaler Bereich sein. Durch die Verwendung von `@simd` bestätigen Sie mehrere Eigenschaften der Schleife:

  * Es ist sicher, Iterationen in beliebiger oder überlappender Reihenfolge auszuführen, wobei besondere Überlegungen für Reduktionsvariablen angestellt werden.
  * Gleitkommaoperationen auf Reduktionsvariablen können umsortiert oder zusammengefasst werden, was möglicherweise andere Ergebnisse als ohne `@simd` zur Folge hat.

In vielen Fällen kann Julia innere `for`-Schleifen automatisch vektorisieren, ohne `@simd` zu verwenden. Die Verwendung von `@simd` gibt dem Compiler ein wenig zusätzlichen Spielraum, um dies in mehr Situationen zu ermöglichen. In jedem Fall sollte Ihre innere Schleife die folgenden Eigenschaften aufweisen, um die Vektorisierung zu ermöglichen:

  * Die Schleife muss eine innerste Schleife sein.
  * Der Schleifeninhalt muss aus geradlinigem Code bestehen. Daher ist [`@inbounds`](@ref) derzeit für alle Array-Zugriffe erforderlich. Der Compiler kann manchmal kurze `&&`, `||` und `?:`-Ausdrücke in geradlinigen Code umwandeln, wenn es sicher ist, alle Operanden bedingungslos auszuwerten. Ziehen Sie in Betracht, die [`ifelse`](@ref)-Funktion anstelle von `?:` in der Schleife zu verwenden, wenn es sicher ist, dies zu tun.
  * Zugriffe müssen ein Sprungmuster haben und dürfen keine "Gathers" (Zugriffe mit zufälligen Indizes) oder "Scatters" (Schreibzugriffe mit zufälligen Indizes) sein.
  * Der Sprung sollte ein Einheitssprung sein.

!!! note
    Das `@simd` behauptet standardmäßig nicht, dass die Schleife vollständig frei von speicherabhängigen Abhängigkeiten ist, was eine Annahme ist, die in generischem Code leicht verletzt werden kann. Wenn Sie nicht-generischen Code schreiben, können Sie `@simd ivdep for ... end` verwenden, um auch zu bestätigen, dass:


  * Es gibt keine speicherabhängigen Abhängigkeiten.
  * Keine Iteration wartet jemals auf eine vorherige Iteration, um Fortschritte zu machen.
