```
require(into::Module, module::Symbol)
```

Diese Funktion ist Teil der Implementierung von [`using`](@ref) / [`import`](@ref), wenn ein Modul noch nicht in `Main` definiert ist. Sie kann auch direkt aufgerufen werden, um das Neuladen eines Moduls zu erzwingen, unabhängig davon, ob es zuvor geladen wurde (zum Beispiel beim interaktiven Entwickeln von Bibliotheken).

Lädt eine Quelldatei im Kontext des `Main`-Moduls auf jedem aktiven Knoten und sucht in den Standardverzeichnissen nach Dateien. `require` wird als eine Top-Level-Operation betrachtet, daher setzt es den aktuellen `include`-Pfad, verwendet ihn jedoch nicht zur Dateisuche (siehe Hilfe für [`include`](@ref)). Diese Funktion wird typischerweise verwendet, um Bibliothekscode zu laden, und wird implizit von `using` aufgerufen, um Pakete zu laden.

Bei der Dateisuche sucht `require` zuerst nach Paketcode im globalen Array [`LOAD_PATH`](@ref). `require` ist auf allen Plattformen, einschließlich solcher mit nicht groß-/kleinschreibungsempfindlichen Dateisystemen wie macOS und Windows, groß-/kleinschreibungsempfindlich.

Für weitere Details zum Laden von Code siehe die Handbuchabschnitte über [Module](@ref modules) und [paralleles Rechnen](@ref code-availability).
