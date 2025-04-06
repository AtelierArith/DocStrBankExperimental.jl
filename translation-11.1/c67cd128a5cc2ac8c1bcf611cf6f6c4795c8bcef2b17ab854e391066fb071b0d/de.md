# Dokumentation

Funktionen, Methoden und Typen können dokumentiert werden, indem man einen String vor der Definition platziert:

```
"""
# Die Foo-Funktion
`foo(x)`: Foo den lebenden Teufel aus `x`.
"""
foo(x) = ...
```

Das `@doc`-Makro kann direkt verwendet werden, um sowohl Dokumentation / Metadaten festzulegen als auch abzurufen. Das Makro hat eine spezielle Syntax, sodass das dokumentierte Objekt in der nächsten Zeile erscheinen kann:

```
@doc "blah"
function foo() ...
```

Standardmäßig wird die Dokumentation als Markdown geschrieben, aber jedes Objekt kann als erstes Argument verwendet werden.

## Dokumentation von Objekten getrennt von ihren Definitionen

Sie können ein Objekt vor oder nach seiner Definition dokumentieren mit

```
@doc "foo" function_to_doc
@doc "bar" TypeToDoc
```

Für Makros lautet die Syntax `@doc "macro doc" :(Module.@macro)` oder `@doc "macro doc" :(string_macro"")` für String-Makros. Ohne das Zitat `:()` wird die Expansion des Makros dokumentiert.

## Abrufen von Dokumentation

Sie können Dokumente für Funktionen, Makros und andere Objekte wie folgt abrufen:

```
@doc foo
@doc @time
@doc md""
```

## Funktionen & Methoden

Das Platzieren von Dokumentation vor einer Methodendefinition (z. B. `function foo() ...` oder `foo() = ...`) bewirkt, dass diese spezifische Methode dokumentiert wird, im Gegensatz zur gesamten Funktion. Methodendokumente werden in der Reihenfolge, in der sie definiert wurden, zusammengefügt, um Dokumente für die Funktion bereitzustellen.
