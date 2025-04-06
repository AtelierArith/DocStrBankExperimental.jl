```
handle_message(logger, level, message, _module, group, id, file, line; key1=val1, ...)
```

Protokolliere eine Nachricht an `logger` auf `level`. Der logische Ort, an dem die Nachricht generiert wurde, wird durch das Modul `_module` und die Gruppe angegeben; der Quellort durch `file` und `line`. `id` ist ein beliebiger eindeutiger Wert (typischerweise ein [`Symbol`](@ref)), der als Schlüssel verwendet wird, um die Protokollanweisung beim Filtern zu identifizieren.
