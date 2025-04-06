```
@static
```

Teile eine Ausdruck zur Parse-Zeit aus.

Zum Beispiel wird `@static Sys.iswindows() ? foo : bar` `Sys.iswindows()` auswerten und entweder `foo` oder `bar` in den Ausdruck einfügen. Dies ist nützlich in Fällen, in denen eine Konstruktion auf anderen Plattformen ungültig wäre, wie ein `ccall` zu einer nicht existierenden Funktion. `@static if Sys.isapple() foo end` und `@static foo <&&,||> bar` sind ebenfalls gültige Syntax.
