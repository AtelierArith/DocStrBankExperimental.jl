```
DateFormat(format::AbstractString, locale="deutsch") -> DateFormat
```

Konstruiere ein Datumsformatierungsobjekt, das zum Parsen von Datumszeichenfolgen oder zum Formatieren eines Datumsobjekts als Zeichenfolge verwendet werden kann. Die folgenden Zeichencodes können verwendet werden, um die `format`-Zeichenfolge zu erstellen:

| Code       | Entspricht | Kommentar                                                                        |
|:---------- |:---------- |:-------------------------------------------------------------------------------- |
| `Y`        | 1996, 96   | Gibt das Jahr 1996, 0096 zurück                                                  |
| `y`        | 1996, 96   | Dasselbe wie `Y` bei `parse`, verwirft jedoch überschüssige Ziffern bei `format` |
| `m`        | 1, 01      | Entspricht 1- oder 2-stelligen Monaten                                           |
| `u`        | Jan        | Entspricht abgekürzten Monaten gemäß dem `locale`-Schlüsselwort                  |
| `U`        | Januar     | Entspricht vollständigen Monatsnamen gemäß dem `locale`-Schlüsselwort            |
| `d`        | 1, 01      | Entspricht 1- oder 2-stelligen Tagen                                             |
| `H`        | 00         | Entspricht Stunden (24-Stunden-Format)                                           |
| `I`        | 00         | Zum Ausgeben von Stunden im 12-Stunden-Format                                    |
| `M`        | 00         | Entspricht Minuten                                                               |
| `S`        | 00         | Entspricht Sekunden                                                              |
| `s`        | .500       | Entspricht Millisekunden                                                         |
| `e`        | Mo, Di     | Entspricht abgekürzten Wochentagen                                               |
| `E`        | Montag     | Entspricht vollständigen Wochentagen                                             |
| `p`        | AM         | Entspricht AM/PM (nicht groß-/kleinschreibungssensitiv)                          |
| `yyyymmdd` | 19960101   | Entspricht festbreitigem Jahr, Monat und Tag                                     |

Zeichen, die oben nicht aufgeführt sind, werden normalerweise als Trennzeichen zwischen Datum und Uhrzeit behandelt. Beispielsweise hätte eine `dt`-Zeichenfolge von "1996-01-15T00:00:00.0" eine `format`-Zeichenfolge wie "y-m-dTH:M:S.s". Wenn du einen Code-Zeichensatz als Trennzeichen verwenden musst, kannst du ihn mit einem Backslash escapen. Das Datum "1995y01m" hätte das Format "y\ym\m".

Beachte, dass 12:00AM 00:00 (Mitternacht) entspricht und 12:00PM 12:00 (Mittag) entspricht. Beim Parsen einer Zeit mit einem `p`-Spezifizierer wird jede Stunde (entweder `H` oder `I`) als 12-Stunden-Format interpretiert, sodass der `I`-Code hauptsächlich für die Ausgabe nützlich ist.

Das Erstellen eines DateFormat-Objekts ist kostspielig. Wann immer möglich, erstelle es einmal und verwende es viele Male oder versuche das [`dateformat""`](@ref @dateformat_str) String-Makro. Die Verwendung dieses Makros erstellt das DateFormat-Objekt einmal zur Makroerweiterungszeit und verwendet es später wieder. Es gibt auch mehrere [vordefinierte Formatter](@ref Common-Date-Formatters), die später aufgelistet sind.

Siehe [`DateTime`](@ref) und [`format`](@ref) für Informationen zur Verwendung eines DateFormat-Objekts zum Parsen und Schreiben von Datumszeichenfolgen.
