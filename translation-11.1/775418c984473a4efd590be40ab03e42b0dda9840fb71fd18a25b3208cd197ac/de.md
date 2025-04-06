```
graphemes(s::AbstractString) -> GraphemeIterator
```

Gibt einen Iterator über Teilstrings von `s` zurück, die den erweiterten Graphemen im String entsprechen, wie sie durch Unicode UAX #29 definiert sind. (Ungefähr sind dies das, was Benutzer als einzelne Zeichen wahrnehmen würden, auch wenn sie mehr als einen Codepunkt enthalten können; zum Beispiel ist ein Buchstabe kombiniert mit einem Akzentzeichen ein einzelner Graphem.)
