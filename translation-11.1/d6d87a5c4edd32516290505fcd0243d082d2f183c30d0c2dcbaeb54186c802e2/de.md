```
RadioMenu
```

Ein Menü, das es einem Benutzer ermöglicht, eine einzelne Option aus einer Liste auszuwählen.

# Beispielausgabe

```julia-repl
julia> request(RadioMenu(options, pagesize=4))
Wählen Sie Ihre Lieblingsfrucht:
^  Traube
   Erdbeere
 > Blaubeere
v  Pfirsich
Ihre Lieblingsfrucht ist Blaubeere!
```
