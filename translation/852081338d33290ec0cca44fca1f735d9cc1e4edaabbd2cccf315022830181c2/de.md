# [Installation](@id man-installation)

Es gibt viele Möglichkeiten, Julia zu installieren. Die folgenden Abschnitte heben die empfohlene Methode für jede der Hauptplattformen hervor und präsentieren dann alternative Möglichkeiten, die in speziellen Situationen nützlich sein könnten.

Die aktuelle Installationsempfehlung ist eine Lösung, die auf Juliaup basiert. Wenn Sie Julia zuvor mit einer Methode installiert haben, die *nicht* auf Juliaup basiert, und Ihr System auf eine Installation umstellen möchten, die auf Juliaup basiert, empfehlen wir, alle vorherigen Julia-Versionen zu deinstallieren, sicherzustellen, dass Sie alles Julia-bezogene aus Ihrer `PATH`-Variablen entfernen, und dann Julia mit einer der unten beschriebenen Methoden zu installieren.

## Windows

Auf Windows kann Julia direkt aus dem Windows Store installiert werden [here](https://www.microsoft.com/store/apps/9NJNWW8PVKMN). Man kann auch genau die gleiche Version installieren, indem man folgendes ausführt

```
winget install julia -s msstore
```

in jeder Shell.

## Mac and Linux

Julia kann auf Linux oder Mac installiert werden, indem man folgendes ausführt

```
curl -fsSL https://install.julialang.org | sh
```

in einer Shell.

### Command line arguments

Man kann verschiedene Befehlszeilenargumente an den Julia-Installer übergeben. Die Syntax für Installer-Argumente ist

```bash
curl -fsSL https://install.julialang.org | sh -s -- <ARGS>
```

Hier sollten `<ARGS>` durch eines oder mehrere der folgenden Argumente ersetzt werden:

  * `--yes` (oder `-y`): Führen Sie den Installer im nicht-interaktiven Modus aus. Alle Konfigurationswerte verwenden ihre Standardwerte oder einen über ein Befehlszeilenargument bereitgestellten Wert.
  * `--default-channel=<NAME>`: Konfigurieren Sie den Standard-Juliaup-Kanal. Zum Beispiel würde `--default-channel lts` den `lts`-Kanal installieren und als Standard konfigurieren.
  * `--add-to-path=<ja|nein>`: Konfigurieren, ob Julia zur `PATH`-Umgebungsvariable hinzugefügt werden soll. Gültige Werte sind `ja` (Standard) und `nein`.
  * `--background-selfupdate=<SECONDS>`: Konfigurieren Sie einen optionalen CRON-Job, der Juliaup automatisch aktualisiert, wenn `<SECONDS>` einen Wert größer als 0 hat. Der tatsächliche Wert steuert, wie oft der CRON-Job in Sekunden ausgeführt wird, um nach einer neuen Juliaup-Version zu suchen. Der Standardwert ist 0, d.h. es wird kein CRON-Job erstellt.
  * `--startup-selfupdate=<MINUTEN>`: Konfigurieren Sie, wie oft Julia beim Start nach neuen Versionen von Juliaup sucht. Der Standardwert beträgt alle 1440 Minuten.
  * `-p=<PATH>` (oder `--path`): Konfigurieren Sie, wo die Julia- und Juliaup-Binärdateien installiert sind. Der Standardwert ist `~/.juliaup`.

## Alternative installation methods

Beachten Sie, dass wir die folgenden Methoden *nur* empfehlen, wenn keine der oben beschriebenen Installationsmethoden für Ihr System funktioniert.

Einige der unten beschriebenen Installationsmethoden empfehlen die Installation eines Pakets namens `juliaup`. Beachten Sie, dass dies dennoch ein voll funktionsfähiges Julia-System installiert, nicht nur Juliaup.

### App Installer (Windows)

Wenn der Windows Store auf einem System blockiert ist, haben wir eine alternative [MSIX App Installer](https://learn.microsoft.com/en-us/windows/msix/app-installer/app-installer-file-overview) basierte Einrichtung. Um die App Installer-Version zu verwenden, laden Sie die [this](https://install.julialang.org/Julia.appinstaller) Datei herunter und öffnen Sie sie, indem Sie doppelt darauf klicken.

### MSI Installer (Windows)

Wenn weder der Windows Store noch die App Installer-Version auf Ihrem Windows-System funktionieren, können Sie auch einen MSI-basierten Installer verwenden. Beachten Sie, dass diese Installationsmethode ernsthafte Einschränkungen mit sich bringt und im Allgemeinen nicht empfohlen wird, es sei denn, keine andere Methode funktioniert. Zum Beispiel gibt es mit dieser Installationsmethode keinen automatischen Aktualisierungsmechanismus für Juliaup. Die 64-Bit-Version des MSI-Installers kann von [here](https://install.julialang.org/Julia-x64.msi) heruntergeladen werden, und die 32-Bit-Version von [here](https://install.julialang.org/Julia-x86.msi).

Standardmäßig wird die Installation als Benutzerinstallation durchgeführt, die keine Erhöhung der Berechtigungen erfordert. Sie können auch eine Systeminstallation durchführen, indem Sie den folgenden Befehl aus einer Shell ausführen:

```
msiexec /i <PATH_TO_JULIA_MSI> ALLUSERS=1
```

### [Homebrew](https://brew.sh) (Mac and Linux)

Auf Systemen mit Brew können Sie Julia installieren, indem Sie Folgendes ausführen

```
brew install juliaup
```

in einer Shell. Beachten Sie, dass Sie Juliaup mit den Standard-Brew-Befehlen aktualisieren müssen.

### [Arch Linux - AUR](https://aur.archlinux.org/packages/juliaup/) (Linux)

Auf Arch Linux ist Juliaup verfügbar [in the Arch User Repository (AUR)](https://aur.archlinux.org/packages/juliaup/).

### [openSUSE Tumbleweed](https://get.opensuse.org/tumbleweed/) (Linux)

Auf openSUSE Tumbleweed können Sie Julia installieren, indem Sie folgendes ausführen

```sh
zypper install juliaup
```

in einer Shell mit Root-Rechten.

### [cargo](https://crates.io/crates/juliaup/) (Windows, Mac and Linux)

Um Julia über Rusts Cargo zu installieren, führen Sie Folgendes aus:

```sh
cargo install juliaup
```
