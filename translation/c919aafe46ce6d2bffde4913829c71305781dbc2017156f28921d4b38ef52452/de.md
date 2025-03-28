# Binary distributions

Diese Notizen sind für diejenigen gedacht, die eine binäre Distribution von Julia für die Verbreitung auf verschiedenen Plattformen erstellen möchten. Wir lieben es, wenn Benutzer Julia so weit und breit wie möglich verbreiten und es auf einer Vielzahl von Betriebssystemen und Hardwarekonfigurationen ausprobieren. Da jede Plattform spezifische Herausforderungen und Prozesse hat, die befolgt werden müssen, um eine tragbare, funktionierende Julia-Distribution zu erstellen, haben wir die meisten Notizen nach Betriebssystemen getrennt.

Beachten Sie, dass der Code für Julia [MIT-licensed, with a few exceptions](https://github.com/JuliaLang/julia/blob/master/LICENSE.md) ist, die Verteilung, die durch die hier beschriebenen Techniken erstellt wird, jedoch unter der GPL-Lizenz steht, da verschiedene abhängige Bibliotheken wie `SuiteSparse` unter der GPL-Lizenz stehen. Wir hoffen, in Zukunft eine nicht-GPL-Verteilung von Julia zu haben.

## Versioning and Git

Die Makefile verwendet sowohl die `VERSION`-Datei als auch Commit-Hashes und Tags aus dem Git-Repository, um die `base/version_git.jl` zu generieren, die Informationen enthält, die wir verwenden, um den Splash-Bildschirm und die Ausgabe von `versioninfo()` zu füllen. Wenn Sie aus irgendeinem Grund das Git-Repository beim Bauen nicht verfügbar haben möchten, sollten Sie die `base/version_git.jl`-Datei vorab generieren mit:

```
make -C base version_git.jl.phony
```

Julia hat viele Build-Abhängigkeiten, bei denen wir gepatchte Versionen verwenden, die noch nicht von den gängigen Paketmanagern aufgenommen wurden. Diese Abhängigkeiten werden normalerweise automatisch heruntergeladen, wenn Sie bauen, aber wenn Sie in der Lage sein möchten, Julia auf einem Computer ohne Internetzugang zu bauen, sollten Sie ein Vollquell-Archiv mit dem speziellen Make-Ziel erstellen.

```
make full-source-dist
```

das ein julia-version-commit.tar.gz-Archiv mit allen erforderlichen Abhängigkeiten erstellt.

Beim Kompilieren eines getaggten Releases im Git-Repository zeigen wir keine Informationen zu Branch/Commit-Hash im Splash-Screen an. Sie können diese Zeile verwenden, um eine Release-Beschreibung von bis zu 45 Zeichen anzuzeigen. Um diese Zeile festzulegen, müssen Sie eine Make.user-Datei erstellen, die Folgendes enthält:

```
override TAGGED_RELEASE_BANNER = "my-package-repository build"
```

## Target Architectures

Standardmäßig optimiert Julia sein System-Image für die native Architektur der Build-Maschine. Dies ist in der Regel nicht das, was Sie beim Erstellen von Paketen möchten, da es dazu führen kann, dass Julia beim Start auf jeder Maschine mit inkompatiblen CPUs (insbesondere älteren mit eingeschränkteren Befehlssätzen) fehlschlägt.

Wir empfehlen daher, dass Sie die `MARCH`-Variable beim Aufruf von `make` übergeben und sie auf das Baseline-Ziel setzen, das Sie unterstützen möchten. Dies bestimmt die Ziel-CPU sowohl für die Julia-Ausführungsdatei als auch für die Bibliotheken und das System-Image (letzteres kann auch mit [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) festgelegt werden). Typischerweise nützliche Werte für x86-CPUs sind `x86-64` und `core2` (für 64-Bit-Bauten) und `pentium4` (für 32-Bit-Bauten). Leider werden CPUs, die älter als Pentium 4 sind, derzeit nicht unterstützt (siehe [this issue](https://github.com/JuliaLang/julia/issues/7185)).

Die vollständige Liste der von LLVM unterstützten CPU-Ziele kann durch Ausführen von `llc -mattr=help` abgerufen werden.

## Linux

Auf Linux erstellt `make binary-dist` ein Tarball, das eine voll funktionsfähige Julia-Installation enthält. Wenn Sie ein Verteilungspaket wie ein `.deb` oder `.rpm` erstellen möchten, sind einige zusätzliche Anstrengungen erforderlich. Siehe das [julia-debian](https://github.com/staticfloat/julia-debian) Repository für ein Beispiel, welche Metadaten für die Erstellung von `.deb`-Paketen für Debian- und Ubuntu-basierte Systeme benötigt werden. Siehe das [Fedora package](https://src.fedoraproject.org/rpms/julia) für RPM-basierte Distributionen. Obwohl wir damit noch nicht experimentiert haben, könnte [Alien](https://wiki.debian.org/Alien) verwendet werden, um Julia-Pakete für verschiedene Linux-Distributionen zu generieren.

Julia unterstützt das Überschreiben der Standardinstallationsverzeichnisse über `prefix` und andere Umgebungsvariablen, die Sie beim Aufruf von `make` und `make install` übergeben können. Siehe Make.inc für ihre Liste. `DESTDIR` kann ebenfalls verwendet werden, um die Installation in ein temporäres Verzeichnis zu erzwingen.

Standardmäßig lädt Julia `$prefix/etc/julia/startup.jl` als installationsweite Initialisierungsdatei. Diese Datei kann von Verteilungsmanagern verwendet werden, um benutzerdefinierte Pfade oder Initialisierungscode einzurichten. Für Linux-Distributionspakete, wenn `$prefix` auf `/usr` gesetzt ist, gibt es kein `/usr/etc`, in das man schauen kann. Dies erfordert, dass der Pfad zum privaten `etc`-Verzeichnis von Julia geändert wird. Dies kann über die `sysconfdir`-Make-Variable beim Bauen erfolgen. Übergeben Sie einfach `sysconfdir=/etc` an `make`, wenn Sie bauen, und Julia wird zuerst `/etc/julia/startup.jl` überprüfen, bevor es `$prefix/etc/julia/startup.jl` versucht.

## OS X

Um eine binäre Verteilung auf OSX zu erstellen, bauen Sie zuerst Julia, wechseln Sie dann in das Verzeichnis `contrib/mac/app` und führen Sie `make` mit denselben Makevars aus, die beim Erstellen von Julia verwendet wurden. Dies erstellt dann eine `.dmg`-Datei im Verzeichnis `contrib/mac/app`, die eine vollständig eigenständige Julia.app enthält.

Alternativ kann Julia als Framework erstellt werden, indem `make` mit dem Ziel `darwinframework` und `DARWIN_FRAMEWORK=1` gesetzt wird. Zum Beispiel `make DARWIN_FRAMEWORK=1 darwinframework`.

## Windows

Anleitungen zum Erstellen einer Julia-Distribution unter Windows sind beschrieben in der [build devdocs for Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md).

## Notes on BLAS and LAPACK

Julia baut OpenBLAS standardmäßig, das die BLAS- und LAPACK-Bibliotheken umfasst. Auf 32-Bit-Architekturen baut Julia OpenBLAS so, dass 32-Bit-Ganzzahlen verwendet werden, während auf 64-Bit-Architekturen Julia OpenBLAS so baut, dass 64-Bit-Ganzzahlen (ILP64) verwendet werden. Es ist wichtig, dass alle Julia-Funktionen, die BLAS- und LAPACK-API-Routinen aufrufen, Ganzzahlen der richtigen Breite verwenden.

Die meisten BLAS- und LAPACK-Distributionen, die auf Linux-Distributionen bereitgestellt werden, und sogar kommerzielle Implementierungen liefern Bibliotheken, die 32-Bit-APIs verwenden. In vielen Fällen wird eine 64-Bit-API als separate Bibliothek bereitgestellt.

Beim Verwenden von vom Anbieter bereitgestellten oder vom Betriebssystem bereitgestellten Bibliotheken ist eine `make`-Option namens `USE_BLAS64` Teil des Julia-Baus verfügbar. Wenn Sie `make USE_BLAS64=0` ausführen, wird Julia BLAS und LAPACK aufrufen, wobei eine 32-Bit-API angenommen wird, bei der alle Ganzzahlen 32-Bit breit sind, selbst auf einer 64-Bit-Architektur.

Andere Bibliotheken, die Julia verwendet, wie SuiteSparse, nutzen ebenfalls intern BLAS und LAPACK. Die APIs müssen über alle Bibliotheken, die von BLAS und LAPACK abhängen, konsistent sein. Der Build-Prozess von Julia wird all diese Bibliotheken korrekt erstellen, aber beim Überschreiben von Standardeinstellungen und der Verwendung von systemeigenen Bibliotheken muss diese Konsistenz gewährleistet sein.

Beachten Sie auch, dass Linux-Distributionen manchmal mehrere Versionen von OpenBLAS ausliefern, von denen einige Multithreading aktivieren und andere nur im seriellen Modus arbeiten. Zum Beispiel ist in Fedora `libopenblasp.so` mehrthreadig, während `libopenblas.so` dies nicht ist. Wir empfehlen, die erstgenannte für optimale Leistung zu verwenden. Um eine OpenBLAS-Bibliothek auszuwählen, deren Name sich von der Standardbibliothek `libopenblas.so` unterscheidet, übergeben Sie `LIBBLAS=-l$(YOURBLAS)` und `LIBBLASNAME=lib$(YOURBLAS)` an `make`, wobei Sie `$(YOURBLAS)` durch den Namen Ihrer Bibliothek ersetzen. Sie können auch `.so.0` zum Namen der Bibliothek hinzufügen, wenn Sie möchten, dass Ihr Paket ohne die unversionierte `.so`-Symlink funktioniert.

Schließlich enthält OpenBLAS seine eigene optimierte Version von LAPACK. Wenn Sie `USE_SYSTEM_BLAS=1` und `USE_SYSTEM_LAPACK=1` setzen, sollten Sie auch `LIBLAPACK=-l$(YOURBLAS)` und `LIBLAPACKNAME=lib$(YOURBLAS)` setzen. Andernfalls wird die Referenz-LAPACK verwendet, und die Leistung wird typischerweise viel niedriger sein.

Ab Julia 1.7 verwendet Julia [libblastrampoline](https://github.com/JuliaLinearAlgebra/libblastrampoline), um zur Laufzeit eine andere BLAS auszuwählen.

# Point releasing 101

Die Erstellung eines Punkt-/Patch-Release besteht aus mehreren unterschiedlichen Schritten.

## Backporting commits

Einige Pull-Requests sind mit "Backport ausstehend x.y" gekennzeichnet, z. B. "Backport ausstehend 0.6". Dies bezeichnet, dass die nächste nachfolgende Version, die aus dem release-x.y-Zweig getaggt wird, die Commit(s) in diesem Pull-Request enthalten sollte(n). Sobald der Pull-Request in den Master gemergt ist, sollte jeder der Commits [cherry picked](https://git-scm.com/docs/git-cherry-pick) in einen speziellen Zweig verschoben werden, der letztendlich in release-x.y gemergt wird.

### Creating a backports branch

Zuerst erstellen Sie einen neuen Branch basierend auf release-x.y. Die übliche Konvention für Julia-Branches besteht darin, den Branch-Namen mit Ihren Initialen zu beginnen, wenn es sich um einen persönlichen Branch handelt. Zum Beispiel nehmen wir an, dass die Autorin des Branches Jane Smith ist.

```
git fetch origin
git checkout release-x.y
git rebase origin/release-x.y
git checkout -b js/backport-x.y
```

Dies stellt sicher, dass Ihre lokale Kopie von release-x.y mit origin auf dem neuesten Stand ist, bevor Sie einen neuen Branch davon erstellen.

### Cherry picking commits

Jetzt führen wir das eigentliche Backporting durch. Finden Sie alle zusammengeführten Pull-Requests, die mit "Backport ausstehend x.y" in der GitHub-Weboberfläche gekennzeichnet sind. Scrollen Sie für jeden dieser Pull-Requests nach unten, wo steht "someperson hat den Commit `123abc` vor XX Minuten in `master` zusammengeführt". Beachten Sie, dass der Commit-Name ein Link ist; wenn Sie darauf klicken, werden Ihnen die Inhalte des Commits angezeigt. Wenn diese Seite zeigt, dass `123abc` ein Merge-Commit ist, gehen Sie zurück zur PR-Seite – wir wollen keine Merge-Commits, wir wollen die tatsächlichen Commits. Wenn dies jedoch keinen Merge-Commit zeigt, bedeutet dies, dass der PR squash-merged wurde. In diesem Fall verwenden Sie die Git-SHA des Commits, die auf dieser Seite neben dem Commit aufgeführt ist.

Sobald Sie den SHA des Commits haben, führen Sie einen Cherry-Pick auf den Backport-Branch durch:

```
git cherry-pick -x -e <sha>
```

Es kann Konflikte geben, die manuell gelöst werden müssen. Sobald die Konflikte gelöst sind (falls zutreffend), fügen Sie einen Verweis auf die GitHub-Pull-Anfrage hinzu, die den Commit im Text der Commit-Nachricht eingeführt hat.

Nachdem alle relevanten Commits im Backports-Branch sind, pushen Sie den Branch zu GitHub.

## Checking for performance regressions

Punktversionen sollten niemals Leistungsrückgänge einführen. Glücklicherweise kann der Julia-Benchmarking-Bot, Nanosoldier, Benchmarks gegen jeden Branch ausführen, nicht nur gegen master. In diesem Fall möchten wir die Benchmark-Ergebnisse von js/backport-x.y gegen release-x.y überprüfen. Um dies zu tun, wecke den Nanosoldier aus seinem robotischen Schlaf mit einem Kommentar zu deinem Backport-Pull-Request:

```markdown
@nanosoldier `runbenchmarks(ALL, vs=":release-x.y")`
```

Dies wird alle registrierten Benchmarks auf release-x.y und js/backport-x.y ausführen und eine Zusammenfassung der Ergebnisse erstellen, wobei alle Verbesserungen und Rückschritte markiert werden.

Wenn Nanosoldier irgendwelche Regressionen findet, versuchen Sie, diese lokal zu überprüfen und Nanosoldier bei Bedarf erneut auszuführen. Wenn die Regressionen als real und nicht nur als Rauschen angesehen werden, müssen Sie einen Commit im Master finden, um diesen zu backporten, falls einer existiert. Andernfalls sollten Sie herausfinden, was die Regression verursacht hat, und einen Patch einreichen (oder jemanden, der den Code kennt, bitten, einen Patch einzureichen) für den Master, und dann den Commit backporten, sobald dieser zusammengeführt wurde. (Oder reichen Sie einen Patch direkt an den Backport-Zweig ein, wenn dies angemessen ist.)

## Building test binaries

Nachdem der Backport-PR in den `release-x.y`-Branch gemergt wurde, aktualisieren Sie Ihre lokale Kopie von Julia und holen Sie sich den SHA des Branches mit

```
git rev-parse origin/release-x.y
```

Halte das bereit, da du es im Feld "Revision" in der Buildbot-Benutzeroberfläche eingeben wirst.

Für jetzt benötigen Sie nur Binärdateien für Linux x86-64, da dies für die Ausführung von PackageEvaluator verwendet wird. Gehen Sie zu https://buildog.julialang.org, reichen Sie einen Job für `nuke_linux64` ein und stellen Sie dann einen Job für `package_linux64` in die Warteschlange, wobei Sie die SHA als Revision angeben. Wenn der Verpackungsjob abgeschlossen ist, wird die Binärdatei in den `julialang2`-Bucket auf AWS hochgeladen. Holen Sie sich die URL, da sie für PackageEvaluator verwendet wird.

## Checking for package breakages

Punktversionen sollten niemals Pakete brechen, mit der möglichen Ausnahme von Paketen, die einige ernsthaft fragwürdige Hacks unter Verwendung von internen Basisfunktionen durchführen, die nicht für die Benutzeroberfläche gedacht sind. (In diesen Fällen sollte man vielleicht ein Wort mit dem Paketautor wechseln.)

Überprüfen, ob Änderungen in der bevorstehenden neuen Version Pakete brechen werden, kann mit [PackageEvaluator](https://github.com/JuliaCI/PackageEvaluator.jl) erfolgen, das oft kurz "PkgEval" genannt wird. PkgEval ist verantwortlich für die Statusabzeichen auf GitHub-Repos und auf pkg.julialang.org. Es läuft typischerweise auf einem der Nicht-Benchmarking-Knoten von Nanosoldier und verwendet Vagrant, um seine Aufgaben in separaten, parallelen VirtualBox-VMs auszuführen.

### Setting up PackageEvaluator

Klonen Sie PackageEvaluator und erstellen Sie einen Branch namens `backport-x.y.z` und checken Sie ihn aus. Beachten Sie, dass die erforderlichen Änderungen etwas hacky und verwirrend sind, und hoffentlich wird das in einer zukünftigen Version von PackageEvaluator angesprochen. Die Änderungen, die vorgenommen werden müssen, orientieren sich an [this commit](https://github.com/JuliaCI/PackageEvaluator.jl/commit/5ba6a3b000e7a3793391d16f695c8704b91d6016).

Das Setup-Skript nimmt sein erstes Argument als die Version von Julia, die ausgeführt werden soll, und das zweite als den Bereich der Paketnamen (AK für Pakete mit den Namen A-K, LZ für L-Z). Die Grundidee ist, dass wir das ein wenig anpassen werden, um nur zwei Versionen von Julia auszuführen, die aktuelle x.y-Version und unsere Backport-Version, jeweils mit drei Bereichen von Paketen.

Im dem verlinkten Diff sagen wir, dass wir, wenn das zweite Argument LZ ist, die aus unserem Backport-Zweig erstellten Binärdateien verwenden, andernfalls (AK) die veröffentlichten Binärdateien. Dann verwenden wir das erste Argument, um einen Abschnitt der Paketliste auszuführen: A-F für Eingabe 0.4, G-N für 0.5 und O-Z für 0.6.

### Running PackageEvaluator

Um PkgEval auszuführen, finden Sie eine ausreichend leistungsstarke Maschine (wie Nanosoldier-Knoten 1), und führen Sie dann aus

```
git clone https://github.com/JuliaCI/PackageEvaluator.jl.git
cd PackageEvaluator.jl/scripts
git checkout backport-x.y.z
./runvagrant.sh
```

Dies erzeugt einige Ordner im Verzeichnis scripts/. Die Ordnernamen und deren Inhalte sind unten decodiert:

| Folder name | Julia version | Package range |
|:-----------:|:-------------:|:-------------:|
|    0.4AK    |    Release    |      A-F      |
|    0.4LZ    |   Backport    |      A-F      |
|    0.5AK    |    Release    |      G-N      |
|    0.5LZ    |   Backport    |      G-N      |
|    0.6AK    |    Release    |      O-Z      |
|    0.6LZ    |   Backport    |      O-Z      |

### Investigating results

Sobald das erledigt ist, können Sie `./summary.sh` aus demselben Verzeichnis verwenden, um einen Zusammenfassungsbericht der Ergebnisse zu erstellen. Wir werden dies für jeden der Ordner tun, um die Gesamtergebnisse nach Version zu aggregieren.

```
./summary.sh 0.4AK/*.json > summary_release.txt
./summary.sh 0.5AK/*.json >> summary_release.txt
./summary.sh 0.6AK/*.json >> summary_release.txt
./summary.sh 0.4LZ/*.json > summary_backport.txt
./summary.sh 0.5LZ/*.json >> summary_backport.txt
./summary.sh 0.6LZ/*.json >> summary_backport.txt
```

Jetzt haben wir zwei Dateien, `summary_release.txt` und `summary_backport.txt`, die die Testergebnisse des PackageEvaluators (Bestanden/Nicht bestanden) für jedes Paket für die beiden Versionen enthalten.

Um diese einfacher in Julia zu verarbeiten, konvertieren wir sie in CSV-Dateien und verwenden dann das DataFrames-Paket, um die Ergebnisse zu verarbeiten. Um in CSV zu konvertieren, kopieren Sie jede .txt-Datei in eine entsprechende .csv-Datei, gehen Sie dann in Vim und führen Sie `ggVGI"<esc>` und dann `:%s/\.json /",/g` aus. (Sie müssen nicht Vim verwenden; das ist nur eine Möglichkeit, es zu tun.) Verarbeiten Sie nun die Ergebnisse mit Julia-Code, der dem folgenden ähnlich ist.

```julia
using DataFrames

release = readtable("summary_release.csv", header=false, names=[:package, :release])
backport = readtable("summary_backport.csv", header=false, names=[:package, :backport])

results = join(release, backport, on=:package, kind=:outer)

for result in eachrow(results)
    a = result[:release]
    b = result[:backport]
    if (isna(a) && !isna(b)) || (isna(b) && !isna(a))
        color = :yellow
    elseif a != b && occursin("pass", b)
        color = :green
    elseif a != b
        color = :red
    else
        continue
    end
    printstyled(result[:package], ": Release ", a, " -> Backport ", b, "\n", color=color)
end
```

Dies wird farbcodierte Zeilen an `stdout` schreiben. Alle Zeilen in Rot müssen untersucht werden, da sie potenzielle Fehler anzeigen, die durch die Backport-Version verursacht wurden. Zeilen in Gelb sollten ebenfalls überprüft werden, da dies bedeutet, dass ein Paket auf einer Version, aber aus irgendeinem Grund nicht auf der anderen lief. Wenn Sie feststellen, dass Ihr zurückportierter Branch Fehler verursacht, verwenden Sie `git bisect`, um die problematischen Commits zu identifizieren, `git revert` diese Commits und wiederholen Sie den Prozess.

## Merging backports into the release branch

Nachdem Sie sichergestellt haben, dass

  * die zurückportierten Commits bestehen alle Unit-Tests von Julia,
  * es gibt keine Leistungsrückgänge, die durch die zurückportierten Commits im Vergleich zum Release-Zweig eingeführt wurden, und
  * die zurückportierten Commits brechen keine registrierten Pakete,

Dann ist der Backport-Zweig bereit, in release-x.y zusammengeführt zu werden. Sobald er zusammengeführt ist, gehe durch und entferne das Label "Backport ausstehend x.y" von allen Pull-Requests, die die zurückportierten Commits enthalten. Entferne das Label nicht von PRs, die nicht zurückportiert wurden.

Der Branch release-x.y sollte jetzt alle neuen Commits enthalten. Das Letzte, was wir mit dem Branch tun möchten, ist, die Versionsnummer anzupassen. Um dies zu tun, reichen Sie einen PR gegen release-x.y ein, der die VERSION-Datei bearbeitet, um `-pre` aus der Versionsnummer zu entfernen. Sobald das zusammengeführt ist, sind wir bereit, zu taggen.

## Tagging the release

Es ist Zeit! Überprüfen Sie den release-x.y Branch und stellen Sie sicher, dass Ihre lokale Kopie des Branches mit dem Remote-Branch auf dem neuesten Stand ist. Führen Sie in der Befehlszeile aus

```
git tag v$(cat VERSION)
git push --tags
```

Dies erstellt das Tag lokal und pusht es zu GitHub.

Nachdem Sie die Version markiert haben, reichen Sie einen weiteren PR an release-x.y ein, um die Patchnummer zu erhöhen und `-pre` wieder am Ende hinzuzufügen. Dies zeigt an, dass der Zustand des Branches eine Vorabversion des nächsten Punkt-Release in der x.y-Serie widerspiegelt.

Befolgen Sie die verbleibenden Anweisungen im Makefile.

## Signing binaries

Einige dieser Schritte erfordern sichere Passwörter. Um die entsprechenden Passwörter zu erhalten, kontaktieren Sie Elliot Saba (staticfloat) oder Alex Arslan (ararslan). Beachten Sie, dass das Code-Signing für jede Plattform auf dieser Plattform durchgeführt werden muss (z. B. muss das Signing für Windows unter Windows erfolgen usw.).

### Linux

Die Codesignierung muss manuell unter Linux durchgeführt werden, ist jedoch recht einfach. Zuerst erhalten Sie die Datei `julia.key` aus dem CodeSigning-Ordner im `juliasecure` AWS-Bucket. Fügen Sie dies mit Ihrem GnuPG-Schlüsselbund hinzu, indem Sie

```
gpg --import julia.key
```

Dies erfordert die Eingabe eines Passworts, das Sie von Elliot oder Alex erhalten müssen. Stellen Sie als Nächstes das Vertrauensniveau für den Schlüssel auf maximal ein. Beginnen Sie mit der Eingabe einer `gpg`-Sitzung:

```
gpg --edit-key julia
```

Geben Sie an der Eingabeaufforderung `trust` ein, und geben Sie dann, wenn Sie nach einem Vertrauensniveau gefragt werden, das maximal verfügbare Niveau an (wahrscheinlich 5). Beenden Sie GnuPG.

Jetzt, für jedes der Linux-Tarballs, die auf den Buildbots erstellt wurden, geben Sie ein

```
gpg -u julia --armor --detach-sig julia-x.y.z-linux-<arch>.tar.gz
```

Dies wird eine entsprechende .asc-Datei für jedes Tarball erzeugen. Und das war's!

### macOS

Code-Signing sollte automatisch auf den macOS-Buildbots erfolgen. Es ist jedoch wichtig zu überprüfen, ob es erfolgreich war. Auf einem System oder einer virtuellen Maschine, die macOS ausführt, laden Sie die .dmg-Datei herunter, die auf den Buildbots erstellt wurde. Zum Beispiel nennen wir die .dmg-Datei `julia-x.y.z-osx.dmg`. Führen Sie aus

```
mkdir ./jlmnt
hdiutil mount -readonly -mountpoint ./jlmnt julia-x.y.z-osx.dmg
codesign -v jlmnt/Julia-x.y.app
```

Stellen Sie sicher, dass Sie den Namen der gemounteten Festplatte notieren, die beim Mounten aufgeführt ist! Zum Beispiel nehmen wir an, dies ist `disk3`. Wenn die Code-Signaturüberprüfung erfolgreich abgeschlossen wurde, gibt es keine Ausgabe vom `codesign`-Schritt. Wenn es tatsächlich erfolgreich war, können Sie die .dmg jetzt abtrennen:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
```

Wenn Sie eine Nachricht wie diese erhalten

> Julia-x.y.app: Der Codeobjekt ist überhaupt nicht signiert.


dann müssen Sie manuell unterschreiben.

Um manuell zu signieren, rufen Sie zuerst die OS X-Zertifikate aus dem CodeSigning-Ordner im `juliasecure`-Bucket auf AWS ab. Fügen Sie die .p12-Datei mit Keychain.app zu Ihrem Schlüsselbund hinzu. Fragen Sie Elliot Saba (staticfloat) oder Alex Arslan (ararslan) nach dem Passwort für den Schlüssel. Führen Sie jetzt aus

```
hdiutil convert julia-x.y.z-osx.dmg -format UDRW -o julia-x.y.z-osx_writable.dmg
mkdir ./jlmnt
hdiutil mount -mountpoint julia-x.y.z-osx_writable.dmg
codesign -s "AFB379C0B4CBD9DB9A762797FC2AB5460A2B0DBE" --deep jlmnt/Julia-x.y.app
```

Dies kann mit einer Nachricht wie fehlschlagen

> Julia-x.y.app: Ressourcengabel, Finder-Informationen oder ähnlicher Abfall nicht erlaubt


Wenn das der Fall ist, müssen Sie überflüssige Attribute entfernen:

```
xattr -cr jlmnt/Julia-x.y.app
```

Dann versuchen Sie erneut, die Code-Signierung durchzuführen. Wenn dabei keine Fehler auftreten, versuchen Sie die Überprüfung erneut. Wenn jetzt alles in Ordnung ist, demontieren Sie das beschreibbare .dmg und konvertieren Sie es zurück in den Nur-Lesen-Modus:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
hdiutil convert julia-x.y.z-osx_writable.dmg -format UDZO -o julia-x.y.z-osx_fixed.dmg
```

Überprüfen Sie, ob das resultierende .dmg tatsächlich repariert ist, indem Sie darauf doppelklicken. Wenn alles gut aussieht, werfen Sie es aus und entfernen Sie das Suffix `_fixed` aus dem Namen. Und das war's!

### Windows

Die Signierung muss manuell unter Windows durchgeführt werden. Zuerst müssen Sie das Windows 10 SDK von der Microsoft-Website herunterladen, das die erforderlichen Signierungswerkzeuge enthält. Wir benötigen das `SignTool`-Dienstprogramm, das normalerweise in einem Verzeichnis wie `C:\Program Files (x86)\Windows Kits\10\App Certification Kit` installiert sein sollte. Holen Sie sich die Windows-Zertifikatdateien von CodeSigning auf `juliasecure` und legen Sie sie im selben Verzeichnis wie die ausführbaren Dateien ab. Öffnen Sie ein Windows CMD-Fenster, wechseln Sie mit `cd` in das Verzeichnis, in dem sich alle Dateien befinden, und führen Sie aus

```
set PATH=%PATH%;C:\Program Files (x86)\Windows Kits\10\App Certification Kit;
signtool sign /f julia-windows-code-sign_2017.p12 /p "PASSWORD" ^
   /t http://timestamp.verisign.com/scripts/timstamp.dll ^
   /v julia-x.y.z-win32.exe
```

Beachten Sie, dass `^` ein Zeilenfortsetzungszeichen in Windows CMD ist und `PASSWORD` ein Platzhalter für das Passwort dieses Zertifikats ist. Wie gewohnt, kontaktieren Sie Elliot oder Alex für Passwörter. Wenn es keine Fehler gibt, ist alles in Ordnung!

## Uploading binaries

Jetzt, da alles unterschrieben ist, müssen wir die Binärdateien in AWS hochladen. Sie können ein Programm wie Cyberduck oder das `aws`-Befehlszeilenwerkzeug verwenden. Die Binärdateien sollten in den `julialang2`-Bucket in die entsprechenden Ordner hochgeladen werden. Zum Beispiel geht Linux x86-64 in `julialang2/bin/linux/x.y`. Stellen Sie sicher, dass Sie die aktuelle `julia-x.y-latest-linux-<arch>.tar.gz`-Datei löschen und sie durch eine Kopie von `julia-x.y.z-linux-<arch>.tar.gz` ersetzen.

Wir müssen auch die Prüfziffern für alles hochladen, was wir erstellt haben, einschließlich der Quell-Tarballs und aller Release-Binärdateien. Das ist einfach:

```
shasum -a 256 julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.sha256
md5sum julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.md5
```

Beachten Sie, dass Sie, wenn Sie diese Befehle auf macOS ausführen, eine sehr leicht unterschiedliche Ausgabe erhalten, die durch das Ansehen einer vorhandenen Datei umformatiert werden kann. Mac-Benutzer müssen außerdem `md5 -r` anstelle von `md5sum` verwenden. Laden Sie die .md5- und .sha256-Dateien in `julialang2/bin/checksums` auf AWS hoch.

Stellen Sie sicher, dass die Berechtigungen für alle hochgeladenen Dateien in AWS auf "Jeder: LESEN" gesetzt sind.

Für jede Datei, die wir hochgeladen haben, müssen wir den Fastly-Cache leeren, damit die Links auf der Website auf die aktualisierten Dateien verweisen. Als Beispiel:

```
curl -X PURGE https://julialang-s3.julialang.org/bin/checksums/julia-x.y.z.sha256
```

Manchmal ist das nicht notwendig, aber es ist trotzdem gut, es zu tun.
