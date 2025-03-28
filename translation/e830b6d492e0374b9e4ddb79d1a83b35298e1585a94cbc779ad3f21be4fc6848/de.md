```
format(dt::TimeType, format::AbstractString; locale="deutsch") -> AbstractString
```

Konstruiere einen String, indem du ein `TimeType`-Objekt verwendest und das bereitgestellte `format` anwendest. Die folgenden Zeichencodes können verwendet werden, um den `format`-String zu erstellen:

| Code | Beispiele | Kommentar                                             |
|:---- |:--------- |:----------------------------------------------------- |
| `y`  | 6         | Numerisches Jahr mit fester Breite                    |
| `Y`  | 1996      | Numerisches Jahr mit minimaler Breite                 |
| `m`  | 1, 12     | Numerischer Monat mit minimaler Breite                |
| `u`  | Jan       | Monatsname auf 3 Zeichen verkürzt gemäß dem `locale`  |
| `U`  | Januar    | Vollständiger Monatsname gemäß dem `locale`-Schlüssel |
| `d`  | 1, 31     | Tag des Monats mit minimaler Breite                   |
| `H`  | 0, 23     | Stunde (24-Stunden-Format) mit minimaler Breite       |
| `M`  | 0, 59     | Minute mit minimaler Breite                           |
| `S`  | 0, 59     | Sekunde mit minimaler Breite                          |
| `s`  | 000, 500  | Millisekunde mit einer minimalen Breite von 3         |
| `e`  | Mo, Di    | Abgekürzte Wochentage                                 |
| `E`  | Montag    | Vollständiger Name des Wochentags                     |

Die Anzahl der aufeinanderfolgenden Codezeichen gibt die Breite des Codes an. Ein Format von `yyyy-mm` gibt an, dass der Code `y` eine Breite von vier haben sollte, während `m` eine Breite von zwei hat. Codes, die numerische Ziffern ergeben, haben einen zugehörigen Modus: feste Breite oder minimale Breite. Der Modus mit fester Breite füllt den Wert mit Nullen auf, wenn er kürzer als die angegebene Breite ist, und kürzt den Wert, wenn er länger ist. Der Modus mit minimaler Breite funktioniert genauso wie der Modus mit fester Breite, außer dass er Werte, die länger als die Breite sind, nicht kürzt.

Beim Erstellen eines `format` kannst du beliebige Nicht-Code-Zeichen als Trennzeichen verwenden. Um beispielsweise den String "1996-01-15T00:00:00" zu erzeugen, könntest du `format`: "yyyy-mm-ddTHH:MM:SS" verwenden. Beachte, dass du, wenn du ein Codezeichen als Literal verwenden musst, das Escape-Zeichen Backslash verwenden kannst. Der String "1996y01m" kann mit dem Format "yyyy\ymm\m" erzeugt werden.
