```
pipeline(from, to, ...)
```

Erstellen Sie eine Pipeline von einer Datenquelle zu einem Ziel. Die Quelle und das Ziel können Befehle, I/O-Streams, Zeichenfolgen oder Ergebnisse anderer `pipeline`-Aufrufe sein. Mindestens ein Argument muss ein Befehl sein. Zeichenfolgen beziehen sich auf Dateinamen. Wenn mehr als zwei Argumente übergeben werden, werden sie von links nach rechts verkettet. Zum Beispiel ist `pipeline(a,b,c)` äquivalent zu `pipeline(pipeline(a,b),c)`. Dies bietet eine prägnantere Möglichkeit, mehrstufige Pipelines anzugeben.

**Beispiele**:

```julia
run(pipeline(`ls`, `grep xyz`))
run(pipeline(`ls`, "out.txt"))
run(pipeline("out.txt", `grep xyz`))
```
