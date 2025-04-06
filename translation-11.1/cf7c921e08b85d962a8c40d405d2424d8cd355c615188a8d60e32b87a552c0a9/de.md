```
dlopen(libfile::AbstractString [, flags::Integer]; throw_error:Bool = true)
```

Lädt eine Shared Library und gibt einen undurchsichtigen Handle zurück.

Die durch die Konstante `dlext` angegebene Erweiterung (`.so`, `.dll` oder `.dylib`) kann aus dem `libfile`-String weggelassen werden, da sie bei Bedarf automatisch angehängt wird. Wenn `libfile` kein absoluter Pfadname ist, werden die Pfade im Array `DL_LOAD_PATH` nach `libfile` durchsucht, gefolgt vom Systemladepfad.

Das optionale Argument flags ist eine bitweise Oder-Verknüpfung von null oder mehr der Werte `RTLD_LOCAL`, `RTLD_GLOBAL`, `RTLD_LAZY`, `RTLD_NOW`, `RTLD_NODELETE`, `RTLD_NOLOAD`, `RTLD_DEEPBIND` und `RTLD_FIRST`. Diese werden, wenn möglich, in die entsprechenden Flags des POSIX (und/oder GNU libc und/oder MacOS) dlopen-Befehls umgewandelt oder ignoriert, wenn die angegebene Funktionalität auf der aktuellen Plattform nicht verfügbar ist. Die Standardflags sind plattformspezifisch. Auf MacOS sind die Standard-`dlopen`-Flags `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`, während sie auf anderen Plattformen `RTLD_LAZY|RTLD_DEEPBIND|RTLD_LOCAL` sind. Eine wichtige Verwendung dieser Flags besteht darin, ein nicht standardmäßiges Verhalten anzugeben, wenn der dynamische Bibliothekslader Bibliotheksreferenzen an exportierte Symbole bindet und ob die gebundenen Referenzen in den lokalen oder globalen Prozessbereich gelegt werden. Zum Beispiel ermöglicht `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`, dass die Symbole der Bibliothek für die Verwendung in anderen Shared Libraries verfügbar sind, was Situationen adressiert, in denen Abhängigkeiten zwischen Shared Libraries bestehen.

Wenn die Bibliothek nicht gefunden werden kann, wirft diese Methode einen Fehler, es sei denn, das Schlüsselwortargument `throw_error` ist auf `false` gesetzt, in diesem Fall gibt diese Methode `nothing` zurück.

!!! note
    Ab Julia 1.6 ersetzt diese Methode Pfade, die mit `@executable_path/` beginnen, durch den Pfad zur Julia-Ausführungsdatei, was relocatable relative-path loads ermöglicht. In Julia 1.5 und früher funktionierte dies nur auf macOS.

