```
edit(function, [types])
edit(module)
```

Bearbeiten Sie die Definition einer Funktion und geben Sie optional ein Tupel von Typen an, um anzugeben, welche Methode bearbeitet werden soll. Für Module öffnen Sie die Hauptquelldatei. Das Modul muss zuerst mit `using` oder `import` geladen werden.

!!! compat "Julia 1.1"
    `edit` für Module erfordert mindestens Julia 1.1.


Um sicherzustellen, dass die Datei an der angegebenen Zeile geöffnet werden kann, müssen Sie möglicherweise zuerst `InteractiveUtils.define_editor` aufrufen.
