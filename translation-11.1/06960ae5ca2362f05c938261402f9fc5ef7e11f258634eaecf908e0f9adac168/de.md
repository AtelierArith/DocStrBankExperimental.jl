```
setenv(command::Cmd, env; dir)
```

Setzen Sie Umgebungsvariablen, die beim Ausführen des angegebenen `command` verwendet werden sollen. `env` ist entweder ein Wörterbuch, das Strings auf Strings abbildet, ein Array von Strings der Form `"var=val"` oder null oder mehr `"var"=>val` Paarargumente. Um die vorhandene Umgebung zu ändern (anstatt sie zu ersetzen), erstellen Sie `env` durch `copy(ENV)` und setzen dann `env["var"]=val` nach Bedarf oder verwenden Sie [`addenv`](@ref).

Das Schlüsselwortargument `dir` kann verwendet werden, um ein Arbeitsverzeichnis für den Befehl anzugeben. `dir` hat standardmäßig das aktuell festgelegte `dir` für `command` (das das aktuelle Arbeitsverzeichnis ist, wenn nicht bereits angegeben).

Siehe auch [`Cmd`](@ref), [`addenv`](@ref), [`ENV`](@ref), [`pwd`](@ref).
