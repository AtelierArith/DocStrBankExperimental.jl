```
styled(content::AbstractString) -> AnnotatedString
```

Konstruiere einen stilisierten String. Innerhalb des Strings wenden `{<specs>:<content>}`-Strukturen die Formatierung auf `<content>` an, gemäß der Liste von durch Kommas getrennten Spezifikationen `<specs>`. Jede Spezifikation kann entweder in Form eines Schriftartnamens, einer Inline-Schriftartspezifikation oder eines `key=value`-Paars vorliegen. Der Wert muss in `{...}` eingeschlossen werden, wenn er eines der Zeichen `,=:{}` enthält.

Dies ist ein funktionales Äquivalent zum [`@styled_str`](@ref) Makro, jedoch ohne Interpolationsmöglichkeiten.
