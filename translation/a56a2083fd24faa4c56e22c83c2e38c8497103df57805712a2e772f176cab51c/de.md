```
codepoint(c::AbstractChar) -> Integer
```

Gibt den Unicode-Codepunkt (eine nicht signierte Ganzzahl) zurück, der dem Zeichen `c` entspricht (oder wirft eine Ausnahme, wenn `c` kein gültiges Zeichen darstellt). Für `Char` ist dies ein `UInt32`-Wert, aber `AbstractChar`-Typen, die nur eine Teilmenge von Unicode darstellen, können eine ganzzahlige Zahl anderer Größe zurückgeben (z. B. `UInt8`).
