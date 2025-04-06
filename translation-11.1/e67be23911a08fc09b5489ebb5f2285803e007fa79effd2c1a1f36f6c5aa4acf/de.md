```
run(command, args...; wait::Bool = true)
```

Führen Sie ein Befehlsobjekt aus, das mit Backticks erstellt wurde (siehe den Abschnitt [Ausführen externer Programme](@ref) im Handbuch). Wirft einen Fehler, wenn etwas schiefgeht, einschließlich des Prozesses, der mit einem Status ungleich null beendet wird (wenn `wait` wahr ist).

Die `args...` ermöglichen es Ihnen, Dateideskriptoren an den Befehl weiterzugeben, und sind wie reguläre Unix-Dateideskriptoren angeordnet (z. B. `stdin, stdout, stderr, FD(3), FD(4)...`).

Wenn `wait` falsch ist, läuft der Prozess asynchron. Sie können später darauf warten und seinen Exit-Status überprüfen, indem Sie `success` auf dem zurückgegebenen Prozessobjekt aufrufen.

Wenn `wait` falsch ist, werden die I/O-Streams des Prozesses an `devnull` geleitet. Wenn `wait` wahr ist, werden die I/O-Streams mit dem übergeordneten Prozess geteilt. Verwenden Sie [`pipeline`](@ref), um die I/O-Umleitung zu steuern.
