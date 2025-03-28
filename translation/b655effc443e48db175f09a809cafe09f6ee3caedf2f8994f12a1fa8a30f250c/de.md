```
LOAD_PATH
```

Ein Array von Pfaden für `using` und `import` Anweisungen, die als Projektumgebungen oder Paketverzeichnisse beim Laden von Code berücksichtigt werden. Es wird basierend auf der [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) Umgebungsvariable befüllt, wenn sie gesetzt ist; andernfalls wird es standardmäßig auf `["@", "@v#.#", "@stdlib"]` gesetzt. Einträge, die mit `@` beginnen, haben spezielle Bedeutungen:

  * `@` bezieht sich auf die "aktuelle aktive Umgebung", deren Anfangswert zunächst durch die [`JULIA_PROJECT`](@ref JULIA_PROJECT) Umgebungsvariable oder die `--project` Befehlszeilenoption bestimmt wird.
  * `@stdlib` erweitert sich zum absoluten Pfad des Standardbibliotheksverzeichnisses der aktuellen Julia-Installation.
  * `@name` bezieht sich auf eine benannte Umgebung, die in Depots gespeichert ist (siehe [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)) unter dem Unterverzeichnis `environments`. Die benannten Umgebungen des Benutzers werden in `~/.julia/environments` gespeichert, sodass `@name` auf die Umgebung in `~/.julia/environments/name` verweisen würde, wenn sie existiert und eine `Project.toml`-Datei enthält. Wenn `name` `#`-Zeichen enthält, werden diese durch die Haupt-, Neben- und Patchkomponenten der Julia-Version ersetzt. Zum Beispiel, wenn Sie Julia 1.2 ausführen, dann erweitert sich `@v#.#` zu `@v1.2` und sucht nach einer Umgebung mit diesem Namen, typischerweise in `~/.julia/environments/v1.2`.

Der vollständig erweiterte Wert von `LOAD_PATH`, der nach Projekten und Paketen durchsucht wird, kann durch den Aufruf der Funktion `Base.load_path()` angezeigt werden.

Siehe auch [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), [`JULIA_PROJECT`](@ref JULIA_PROJECT), [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) und [Code Loading](@ref code-loading).
