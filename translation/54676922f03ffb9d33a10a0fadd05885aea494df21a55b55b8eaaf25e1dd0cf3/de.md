```
ConsoleLogger([stream,] min_level=Info; meta_formatter=default_metafmt,
              show_limited=true, right_justify=0)
```

Logger mit Formatierung, die für die Lesbarkeit in einer Textkonsole optimiert ist, zum Beispiel für interaktive Arbeiten mit der Julia REPL.

Protokollebene, die kleiner als `min_level` ist, wird herausgefiltert.

Die Nachrichtenformatierung kann durch das Setzen von Schlüsselwortargumenten gesteuert werden:

  * `meta_formatter` ist eine Funktion, die die Protokollereignis-Metadaten `(level, _module, group, id, file, line)` entgegennimmt und eine Farbe (wie sie an printstyled übergeben werden würde), ein Präfix und ein Suffix für die Protokollnachricht zurückgibt. Der Standard ist, mit der Protokollebene zu prefixen und ein Suffix mit dem Modul, der Datei und der Zeilenposition zu verwenden.
  * `show_limited` begrenzt das Drucken großer Datenstrukturen auf etwas, das auf den Bildschirm passt, indem der `:limit` `IOContext`-Schlüssel während der Formatierung gesetzt wird.
  * `right_justify` ist die ganze Zahl, bei der die Protokollmetadaten rechtsbündig ausgerichtet sind. Der Standardwert ist null (Metadaten stehen in ihrer eigenen Zeile).
