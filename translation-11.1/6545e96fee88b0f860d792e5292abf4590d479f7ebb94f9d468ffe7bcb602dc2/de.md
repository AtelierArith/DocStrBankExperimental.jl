```
arg_write(f::Function, arg::ArgWrite) -> arg
arg_write(f::Function, arg::Nothing) -> tempname()
```

Die Funktion `arg_read` akzeptiert ein Argument `arg`, das eines der folgenden sein kann:

  * `AbstractString`: ein Dateipfad, der zum Schreiben geöffnet werden soll
  * `AbstractCmd`: ein auszuführender Befehl, der in seine Standard-Eingabe schreibt
  * `IO`: ein offenes IO-Handle, in das geschrieben werden soll
  * `Nothing`: ein temporärer Pfad, in den geschrieben werden soll

Wenn der Körper normal zurückkehrt, wird ein geöffneter Pfad nach Abschluss geschlossen; ein IO-Handle-Argument bleibt offen, wird aber vor der Rückkehr geleert. Wenn das Argument `nothing` ist, wird ein temporärer Pfad zum Schreiben geöffnet und nach Abschluss geschlossen, und der Pfad wird von `arg_write` zurückgegeben. In allen anderen Fällen wird `arg` selbst zurückgegeben. Dies ist ein nützliches Muster, da Sie konsistent zurückgeben können, was auch immer geschrieben wurde, unabhängig davon, ob ein Argument übergeben wurde oder nicht.

Wenn während der Auswertung des Körpers ein Fehler auftritt, wird ein von `arg_write` zum Schreiben geöffneter Pfad gelöscht, unabhängig davon, ob er als Zeichenfolge übergeben wurde oder ein temporärer Pfad generiert wurde, wenn `arg` `nothing` ist.

Hinweis: Beim Öffnen einer Datei wird ArgTools `lock = false` an den Aufruf `open(...)` übergeben. Daher sollte das von dieser Funktion zurückgegebene Objekt nicht von mehreren Threads verwendet werden. Diese Einschränkung könnte in Zukunft gelockert werden, was keinen funktionierenden Code brechen würde.
