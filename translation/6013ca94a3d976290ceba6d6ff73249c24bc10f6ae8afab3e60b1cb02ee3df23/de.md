```
add!(repo::GitRepo, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
add!(idx::GitIndex, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
```

Fügen Sie alle Dateien mit den in `files` angegebenen Pfaden zum Index `idx` (oder dem Index des `repo`) hinzu. Wenn die Datei bereits vorhanden ist, wird der Indexeintrag aktualisiert. Wenn die Datei noch nicht vorhanden ist, wird sie neu in den Index aufgenommen. `files` kann Platzhalter enthalten, die erweitert werden, und alle übereinstimmenden Dateien werden hinzugefügt (es sei denn, `INDEX_ADD_DISABLE_PATHSPEC_MATCH` ist gesetzt, siehe unten). Wenn eine Datei ignoriert wurde (in `.gitignore` oder in der Konfiguration), wird sie *nicht* hinzugefügt, *es sei denn*, sie wird bereits im Index verfolgt, in diesem Fall wird sie *aktualisiert*. Das Schlüsselwortargument `flags` ist eine Menge von Bit-Flags, die das Verhalten in Bezug auf ignorierte Dateien steuern:

  * `Consts.INDEX_ADD_DEFAULT` - Standard, oben beschrieben.
  * `Consts.INDEX_ADD_FORCE` - ignoriert die bestehenden Ignorierregeln und erzwingt die Hinzufügung der Datei zum Index, auch wenn sie bereits ignoriert wird.
  * `Consts.INDEX_ADD_CHECK_PATHSPEC` - kann nicht gleichzeitig mit `INDEX_ADD_FORCE` verwendet werden. Überprüfen Sie, dass jede Datei in `files`, die auf der Festplatte vorhanden ist, nicht in der Ignorierliste ist. Wenn eine der Dateien *ignoriert* wird, gibt die Funktion `EINVALIDSPEC` zurück.
  * `Consts.INDEX_ADD_DISABLE_PATHSPEC_MATCH` - deaktiviert die Platzhalterübereinstimmung und fügt nur Dateien zum Index hinzu, die genau mit den in `files` angegebenen Pfaden übereinstimmen.
