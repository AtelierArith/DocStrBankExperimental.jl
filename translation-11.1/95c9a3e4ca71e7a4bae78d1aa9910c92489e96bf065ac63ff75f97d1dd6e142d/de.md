```
define_editor(fn, pattern; wait=false)
```

Definiere einen neuen Editor, der dem `pattern` entspricht und verwendet werden kann, um eine Datei (möglicherweise an einer bestimmten Zeilennummer) mit `fn` zu öffnen.

Das Argument `fn` ist eine Funktion, die bestimmt, wie eine Datei mit dem gegebenen Editor geöffnet werden soll. Es sollte vier Argumente annehmen, wie folgt:

  * `cmd` - ein Basisbefehl-Objekt für den Editor
  * `path` - der Pfad zur zu öffnenden Quelldatei
  * `line` - die Zeilennummer, an der der Editor geöffnet werden soll
  * `column` - die Spaltennummer, an der der Editor geöffnet werden soll

Editoren, die nicht zu einer bestimmten Zeile mit einem Befehl oder einer bestimmten Spalte öffnen können, dürfen das Argument `line` und/oder `column` ignorieren. Der `fn`-Callback muss entweder ein passendes `Cmd`-Objekt zurückgeben, um eine Datei zu öffnen, oder `nothing`, um anzuzeigen, dass sie diese Datei nicht bearbeiten können. Verwende `nothing`, um anzuzeigen, dass dieser Editor für die aktuelle Umgebung nicht geeignet ist und ein anderer Editor versucht werden sollte. Es ist möglich, allgemeinere Bearbeitungs-Hooks hinzuzufügen, die keine externen Befehle auslösen müssen, indem ein Callback direkt in den Vektor `EDITOR_CALLBACKS` eingefügt wird.

Das Argument `pattern` ist eine Zeichenkette, ein regulärer Ausdruck oder ein Array von Zeichenfolgen und regulären Ausdrücken. Damit `fn` aufgerufen wird, muss eines der Muster mit dem Wert von `EDITOR`, `VISUAL` oder `JULIA_EDITOR` übereinstimmen. Bei Zeichenfolgen muss die Zeichenfolge dem [`basename`](@ref) des ersten Wortes des Editorbefehls entsprechen, wobei die Erweiterung, falls vorhanden, entfernt wird. Zum Beispiel passt "vi" nicht zu "vim -g", aber zu "/usr/bin/vi -m"; es passt auch zu `vi.exe`. Wenn `pattern` ein Regex ist, wird es gegen den gesamten Editorbefehl als shell-escaped Zeichenfolge abgeglichen. Ein Array-Muster passt, wenn eines seiner Elemente übereinstimmt. Wenn mehrere Editoren übereinstimmen, wird der zuletzt hinzugefügte verwendet.

Standardmäßig wartet Julia nicht darauf, dass der Editor schließt, und führt ihn im Hintergrund aus. Wenn der Editor jedoch terminalbasiert ist, möchtest du wahrscheinlich `wait=true` setzen, und Julia wartet darauf, dass der Editor schließt, bevor es fortfährt.

Wenn eine der Editor-Umgebungsvariablen gesetzt ist, aber kein Editor-Eintrag übereinstimmt, wird der Standard-Editor-Eintrag aufgerufen:

```
(cmd, path, line, column) -> `$cmd $path`
```

Beachte, dass viele Editoren bereits definiert sind. Alle folgenden Befehle sollten bereits funktionieren:

  * emacs
  * emacsclient
  * vim
  * nvim
  * nano
  * micro
  * kak
  * helix
  * textmate
  * mate
  * kate
  * subl
  * atom
  * notepad++
  * Visual Studio Code
  * open
  * pycharm
  * bbedit

# Beispiele

Das folgende definiert die Verwendung von terminalbasiertem `emacs`:

```
define_editor(
    r"\bemacs\b.*\s(-nw|--no-window-system)\b", wait=true) do cmd, path, line
    `$cmd +$line $path`
end
```

!!! compat "Julia 1.4"
    `define_editor` wurde in Julia 1.4 eingeführt.

