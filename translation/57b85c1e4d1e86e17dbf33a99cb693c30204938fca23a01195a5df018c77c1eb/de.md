```
escape_raw_string(s::AbstractString, delim='"') -> AbstractString
escape_raw_string(io, s::AbstractString, delim='"')
```

Ent escape a string auf die Weise, die für das Parsen von rohen String-Literalen verwendet wird. Für jedes doppelte Anführungszeichen (`"`) im Eingabestring `s` (oder `delim`, falls angegeben) zählt diese Funktion die Anzahl *n* der vorhergehenden Rückwärtsschläge (`\`) und erhöht dann die Anzahl der Rückwärtsschläge von *n* auf 2*n*+1 (auch für *n* = 0). Sie verdoppelt auch eine Folge von Rückwärtsschlägen am Ende des Strings.

Diese Escape-Konvention wird in rohen Strings und anderen nicht standardmäßigen String-Literalen verwendet. (Es ist auch die Escape-Konvention, die vom Microsoft C/C++ Compiler-Laufzeitumgebung erwartet wird, wenn sie einen Befehlszeilenstring in das argv[]-Array parst.)

Siehe auch [`escape_string`](@ref).
