```
MultiSelectMenu
```

Ein Menü, das es einem Benutzer ermöglicht, mehrere Optionen aus einer Liste auszuwählen.

# Beispielausgabe

```julia-repl
julia> request(MultiSelectMenu(options))
Wählen Sie die Früchte aus, die Sie mögen:
[drücken: Enter=umschalten, a=alle, n=keine, d=fertig, q=abbrechen]
   [ ] Apfel
 > [X] Orange
   [X] Traube
   [ ] Erdbeere
   [ ] Blaubeere
   [X] Pfirsich
   [ ] Zitrone
   [ ] Limette
Sie mögen die folgenden Früchte:
  - Orange
  - Traube
  - Pfirsich
```
