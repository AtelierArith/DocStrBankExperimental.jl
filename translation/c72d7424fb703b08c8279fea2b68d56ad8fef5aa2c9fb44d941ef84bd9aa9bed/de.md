# macOS

Sie müssen die aktuellen Xcode-Befehlszeilenwerkzeuge installiert haben: Führen Sie `xcode-select --install` im Terminal aus. Sie müssen diesen Terminalbefehl nach jedem macOS-Update erneut ausführen, andernfalls können Sie auf Fehler stoßen, die mit fehlenden Bibliotheken oder Headern zu tun haben.

Die abhängigen Bibliotheken werden jetzt mit [BinaryBuilder](https://binarybuilder.org) erstellt und werden automatisch heruntergeladen. Dies ist die bevorzugte Methode, um den Julia-Quellcode zu erstellen. Falls Sie sie alle selbst erstellen möchten, benötigen Sie einen 64-Bit gfortran, um die Julia-Abhängigkeiten zu kompilieren.

```bash
brew install gcc
```

Wenn Sie `LD_LIBRARY_PATH` oder `DYLD_LIBRARY_PATH` in Ihrer `.bashrc` oder einer entsprechenden Datei gesetzt haben, kann Julia möglicherweise verschiedene Bibliotheken, die mit ihr gebündelt sind, nicht finden. Diese Umgebungsvariablen müssen deaktiviert werden, damit Julia funktioniert.
