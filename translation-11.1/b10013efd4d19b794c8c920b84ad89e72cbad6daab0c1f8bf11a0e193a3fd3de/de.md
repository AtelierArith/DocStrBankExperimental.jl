```
Cmd(cmd::Cmd; ignorestatus, detach, windows_verbatim, windows_hide, env, dir)
Cmd(exec::Vector{String})
```

Konstruiere ein neues `Cmd`-Objekt, das ein externes Programm und Argumente aus `cmd` darstellt, während die Einstellungen der optionalen Schlüsselwortargumente geändert werden:

  * `ignorestatus::Bool`: Wenn `true` (Standardwert ist `false`), wird der `Cmd` keinen Fehler auslösen, wenn der Rückgabecode ungleich null ist.
  * `detach::Bool`: Wenn `true` (Standardwert ist `false`), wird der `Cmd` in einer neuen Prozessgruppe ausgeführt, sodass er länger als der `julia`-Prozess lebt und kein Ctrl-C an ihn weitergegeben wird.
  * `windows_verbatim::Bool`: Wenn `true` (Standardwert ist `false`), sendet der `Cmd` unter Windows eine Befehlszeilenzeichenfolge an den Prozess, ohne Argumente zu zitieren oder zu escapen, selbst Argumente, die Leerzeichen enthalten. (Unter Windows werden Argumente als eine einzige "Befehlszeilen"-Zeichenfolge an ein Programm gesendet, und Programme sind dafür verantwortlich, sie in Argumente zu parsen. Standardmäßig werden leere Argumente und Argumente mit Leerzeichen oder Tabs in der Befehlszeile mit doppelten Anführungszeichen `"` zitiert, und `\` oder `"` werden mit Backslashes vorangestellt. `windows_verbatim=true` ist nützlich, um Programme zu starten, die ihre Befehlszeile auf nicht standardmäßige Weise parsen.) Hat keine Auswirkungen auf Nicht-Windows-Systeme.
  * `windows_hide::Bool`: Wenn `true` (Standardwert ist `false`), wird unter Windows kein neues Konsolenfenster angezeigt, wenn der `Cmd` ausgeführt wird. Dies hat keine Auswirkungen, wenn bereits ein Konsolenfenster geöffnet ist oder auf Nicht-Windows-Systemen.
  * `env`: Setze Umgebungsvariablen, die beim Ausführen des `Cmd` verwendet werden sollen. `env` ist entweder ein Wörterbuch, das Strings auf Strings abbildet, ein Array von Strings der Form `"var=val"`, ein Array oder Tupel von `"var"=>val`-Paaren. Um die bestehende Umgebung zu modifizieren (anstatt sie zu ersetzen), initialisiere `env` mit `copy(ENV)` und setze dann `env["var"]=val` nach Bedarf. Um einem Umgebungsblock innerhalb eines `Cmd`-Objekts hinzuzufügen, ohne alle Elemente zu ersetzen, verwende [`addenv()`](@ref), das ein `Cmd`-Objekt mit der aktualisierten Umgebung zurückgibt.
  * `dir::AbstractString`: Gib ein Arbeitsverzeichnis für den Befehl an (anstatt des aktuellen Verzeichnisses).

Für alle nicht angegebenen Schlüsselwörter werden die aktuellen Einstellungen von `cmd` verwendet.

Beachte, dass der `Cmd(exec)`-Konstruktor keine Kopie von `exec` erstellt. Alle nachfolgenden Änderungen an `exec` werden im `Cmd`-Objekt widergespiegelt.

Die gebräuchlichste Methode zur Konstruktion eines `Cmd`-Objekts erfolgt mit Befehlsliteralen (Backticks), z. B.

```
`ls -l`
```

Dies kann dann an den `Cmd`-Konstruktor übergeben werden, um seine Einstellungen zu ändern, z. B.

```
Cmd(`echo "Hello world"`, ignorestatus=true, detach=false)
```
