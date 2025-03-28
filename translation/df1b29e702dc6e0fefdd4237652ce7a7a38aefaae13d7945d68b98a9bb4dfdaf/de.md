```
arg_read(f::Function, arg::ArgRead) -> f(arg_io)
```

Die Funktion `arg_read` akzeptiert ein Argument `arg`, das eines der folgenden sein kann:

  * `AbstractString`: ein Dateipfad, der zum Lesen geöffnet werden soll
  * `AbstractCmd`: ein Befehl, der ausgeführt wird und von seiner Standardausgabe liest
  * `IO`: ein offenes IO-Handle, von dem gelesen werden soll

Ob der Körper normal zurückkehrt oder einen Fehler auslöst, ein geöffneter Pfad wird vor der Rückkehr von `arg_read` geschlossen und ein `IO`-Handle wird geleert, aber nicht geschlossen, bevor von `arg_read` zurückgekehrt wird.

Hinweis: Beim Öffnen einer Datei wird ArgTools `lock = false` an den Datei-`open(...)`-Aufruf übergeben. Daher sollte das von dieser Funktion zurückgegebene Objekt nicht von mehreren Threads verwendet werden. Diese Einschränkung könnte in Zukunft gelockert werden, was keinen funktionierenden Code brechen würde.
