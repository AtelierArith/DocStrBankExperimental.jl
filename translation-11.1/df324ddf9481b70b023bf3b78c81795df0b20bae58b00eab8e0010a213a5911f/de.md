# [Code Loading](@id code-loading)

!!! note
    Dieses Kapitel behandelt die technischen Details des Paketladens. Um Pakete zu installieren, verwenden Sie [`Pkg`](@ref Pkg), Julias integrierten Paketmanager, um Pakete zu Ihrer aktiven Umgebung hinzuzufügen. Um Pakete, die bereits in Ihrer aktiven Umgebung sind, zu verwenden, schreiben Sie `import X` oder `using X`, wie im [Modules documentation](@ref modules) beschrieben.


## Definitions

Julia hat zwei Mechanismen zum Laden von Code:

1. **Code-Einbindung:** z.B. `include("source.jl")`. Die Einbindung ermöglicht es Ihnen, ein einzelnes Programm über mehrere Quelldateien zu verteilen. Der Ausdruck `include("source.jl")` bewirkt, dass der Inhalt der Datei `source.jl` im globalen Geltungsbereich des Moduls ausgewertet wird, in dem der `include`-Aufruf erfolgt. Wenn `include("source.jl")` mehrfach aufgerufen wird, wird `source.jl` mehrfach ausgewertet. Der eingeschlossene Pfad, `source.jl`, wird relativ zu der Datei interpretiert, in der der `include`-Aufruf erfolgt. Dies macht es einfach, einen Teilbaum von Quelldateien zu verschieben. Im REPL werden eingeschlossene Pfade relativ zum aktuellen Arbeitsverzeichnis interpretiert, [`pwd()`](@ref).
2. **Paketladen:** z.B. `import X` oder `using X`. Der Importmechanismus ermöglicht es Ihnen, ein Paket zu laden – d.h. eine unabhängige, wiederverwendbare Sammlung von Julia-Code, die in einem Modul verpackt ist – und macht das resultierende Modul im importierenden Modul unter dem Namen `X` verfügbar. Wenn dasselbe `X`-Paket mehrmals in derselben Julia-Sitzung importiert wird, wird es nur beim ersten Mal geladen – bei nachfolgenden Importen erhält das importierende Modul eine Referenz auf dasselbe Modul. Beachten Sie jedoch, dass `import X` in verschiedenen Kontexten unterschiedliche Pakete laden kann: `X` kann sich auf ein Paket namens `X` im Hauptprojekt beziehen, aber möglicherweise auch auf verschiedene Pakete, die ebenfalls `X` heißen, in jeder Abhängigkeit. Mehr dazu unten.

Code-Einbindung ist ziemlich einfach und unkompliziert: Sie bewertet die gegebene Quelldatei im Kontext des Aufrufers. Das Laden von Paketen basiert auf der Code-Einbindung und dient einem [different purpose](@ref modules). Der Rest dieses Kapitels konzentriert sich auf das Verhalten und die Mechanik des Paketladens.

Ein *Paket* ist ein Quellbaum mit einem standardisierten Layout, das Funktionalität bereitstellt, die von anderen Julia-Projekten wiederverwendet werden kann. Ein Paket wird durch die Anweisungen `import X` oder `using X` geladen. Diese Anweisungen machen auch das Modul mit dem Namen `X`—das aus dem Laden des Paketcodes resultiert—innerhalb des Moduls verfügbar, in dem die Importanweisung erfolgt. Die Bedeutung von `X` in `import X` ist kontextabhängig: welches `X`-Paket geladen wird, hängt davon ab, in welchem Code die Anweisung vorkommt. Daher erfolgt die Handhabung von `import X` in zwei Phasen: Zuerst wird bestimmt, **welches** Paket in diesem Kontext als `X` definiert ist; zweitens wird bestimmt, **wo** sich dieses spezielle `X`-Paket befindet.

Diese Fragen werden beantwortet, indem in den Projektumgebungen gesucht wird, die in [`LOAD_PATH`](@ref) aufgeführt sind, nach Projektdateien (`Project.toml` oder `JuliaProject.toml`), Manifestdateien (`Manifest.toml` oder `JuliaManifest.toml`, oder denselben Namen, die mit `-v{major}.{minor}.toml` für spezifische Versionen enden) oder Ordnern mit Quelldateien.

## Federation of packages

Die meiste Zeit ist ein Paket allein durch seinen Namen eindeutig identifizierbar. Manchmal kann es jedoch vorkommen, dass ein Projekt in eine Situation gerät, in der es zwei verschiedene Pakete mit demselben Namen verwenden muss. Während es möglich sein könnte, dies zu beheben, indem man eines der Pakete umbenennt, kann es sehr störend sein, gezwungen zu sein, dies in einem großen, gemeinsam genutzten Codebasis zu tun. Stattdessen ermöglicht Julias Code-Lade-Mechanismus, dass derselbe Paketname auf verschiedene Pakete in verschiedenen Komponenten einer Anwendung verweist.

Julia unterstützt föderiertes Paketmanagement, was bedeutet, dass mehrere unabhängige Parteien sowohl öffentliche als auch private Pakete und Registries von Paketen verwalten können und dass Projekte von einer Mischung aus öffentlichen und privaten Paketen aus verschiedenen Registries abhängen können. Pakete aus verschiedenen Registries werden mit einem gemeinsamen Satz von Tools und Workflows installiert und verwaltet. Der `Pkg` Paketmanager, der mit Julia geliefert wird, ermöglicht es Ihnen, die Abhängigkeiten Ihrer Projekte zu installieren und zu verwalten. Er hilft beim Erstellen und Bearbeiten von Projektdateien (die beschreiben, von welchen anderen Projekten Ihr Projekt abhängt) und Manifestdateien (die exakte Versionen des vollständigen Abhängigkeitsgraphen Ihres Projekts festhalten).

Eine Konsequenz der Föderation ist, dass es keine zentrale Autorität für die Benennung von Paketen geben kann. Verschiedene Entitäten können denselben Namen verwenden, um sich auf nicht verwandte Pakete zu beziehen. Diese Möglichkeit ist unvermeidlich, da diese Entitäten nicht koordiniert sind und möglicherweise nicht einmal voneinander wissen. Aufgrund des Fehlens einer zentralen Benennungsbehörde kann es vorkommen, dass ein einzelnes Projekt von verschiedenen Paketen abhängt, die denselben Namen haben. Julias Paketlade-Mechanismus erfordert nicht, dass Paketnamen global eindeutig sind, selbst innerhalb des Abhängigkeitsgraphen eines einzelnen Projekts. Stattdessen werden Pakete durch [universally unique identifiers](https://en.wikipedia.org/wiki/Universally_unique_identifier) (UUIDs) identifiziert, die bei der Erstellung jedes Pakets zugewiesen werden. In der Regel müssen Sie nicht direkt mit diesen etwas umständlichen 128-Bit-Identifikatoren arbeiten, da `Pkg` sich um die Generierung und Verfolgung dieser für Sie kümmert. Diese UUIDs bieten jedoch die definitive Antwort auf die Frage *"Auf welches Paket bezieht sich `X`?"*

Da das Problem der dezentralen Namensgebung etwas abstrakt ist, kann es hilfreich sein, ein konkretes Szenario durchzugehen, um das Problem zu verstehen. Angenommen, Sie entwickeln eine Anwendung namens `App`, die zwei Pakete verwendet: `Pub` und `Priv`. `Priv` ist ein privates Paket, das Sie erstellt haben, während `Pub` ein öffentliches Paket ist, das Sie verwenden, aber nicht kontrollieren. Als Sie `Priv` erstellt haben, gab es kein öffentliches Paket mit dem Namen `Priv`. Später wurde jedoch ein nicht verwandtes Paket mit dem Namen `Priv` veröffentlicht und ist populär geworden. Tatsächlich hat das `Pub`-Paket begonnen, es zu verwenden. Daher wird `App`, wenn Sie das nächste Mal `Pub` aktualisieren, um die neuesten Fehlerbehebungen und Funktionen zu erhalten, von zwei verschiedenen Paketen namens `Priv` abhängen – ohne dass Sie etwas anderes tun müssen, als ein Upgrade durchzuführen. `App` hat eine direkte Abhängigkeit von Ihrem privaten `Priv`-Paket und eine indirekte Abhängigkeit, über `Pub`, von dem neuen öffentlichen `Priv`-Paket. Da diese beiden `Priv`-Pakete unterschiedlich sind, aber beide erforderlich sind, damit `App` weiterhin korrekt funktioniert, muss der Ausdruck `import Priv` je nachdem, ob er im Code von `App` oder im Code von `Pub` vorkommt, auf unterschiedliche `Priv`-Pakete verweisen. Um dies zu handhaben, unterscheidet Julias Paketlade-Mechanismus die beiden `Priv`-Pakete anhand ihrer UUID und wählt das richtige basierend auf seinem Kontext (dem Modul, das `import` aufgerufen hat). Wie diese Unterscheidung funktioniert, wird durch Umgebungen bestimmt, wie in den folgenden Abschnitten erklärt.

## Environments

Eine *Umgebung* bestimmt, was `import X` und `using X` in verschiedenen Code-Kontexten bedeuten und welche Dateien durch diese Anweisungen geladen werden. Julia versteht zwei Arten von Umgebungen:

1. **Eine Projektumgebung** ist ein Verzeichnis mit einer Projektdatei und einer optionalen Manifestdatei und bildet eine *explizite Umgebung*. Die Projektdatei bestimmt, was die Namen und Identitäten der direkten Abhängigkeiten eines Projekts sind. Die Manifestdatei, falls vorhanden, gibt einen vollständigen Abhängigkeitsgraphen an, einschließlich aller direkten und indirekten Abhängigkeiten, der genauen Versionen jeder Abhängigkeit und ausreichender Informationen, um die richtige Version zu finden und zu laden.
2. **Ein Paketverzeichnis** ist ein Verzeichnis, das die Quellbäume einer Reihe von Paketen als Unterverzeichnisse enthält und eine *implizite Umgebung* bildet. Wenn `X` ein Unterverzeichnis eines Paketverzeichnisses ist und `X/src/X.jl` existiert, dann ist das Paket `X` in der Umgebung des Paketverzeichnisses verfügbar und `X/src/X.jl` ist die Quelldatei, durch die es geladen wird.

Diese können kombiniert werden, um **eine gestapelte Umgebung** zu schaffen: eine geordnete Menge von Projektumgebungen und Paketverzeichnissen, die übereinandergelegt werden, um eine einzige zusammengesetzte Umgebung zu bilden. Die Vorrang- und Sichtbarkeitsregeln bestimmen dann, welche Pakete verfügbar sind und wo sie geladen werden. Julias Ladepfad bildet beispielsweise eine gestapelte Umgebung.

Diese Umgebungen dienen jeweils einem anderen Zweck:

  * Projektumgebungen bieten **Reproduzierbarkeit**. Indem Sie eine Projektumgebung in die Versionskontrolle einpflegen – z. B. in ein Git-Repository – zusammen mit dem restlichen Quellcode des Projekts, können Sie den genauen Zustand des Projekts und aller seiner Abhängigkeiten reproduzieren. Die Manifestdatei erfasst insbesondere die genaue Version jeder Abhängigkeit, die durch einen kryptografischen Hash ihres Quellbaums identifiziert wird, was es `Pkg` ermöglicht, die richtigen Versionen abzurufen und sicherzustellen, dass Sie den genauen Code ausführen, der für alle Abhängigkeiten aufgezeichnet wurde.
  * Paketverzeichnisse bieten **Bequemlichkeit**, wenn eine vollständig sorgfältig verfolgte Projektumgebung nicht erforderlich ist. Sie sind nützlich, wenn Sie eine Reihe von Paketen an einem Ort ablegen und sie direkt verwenden möchten, ohne eine Projektumgebung für sie erstellen zu müssen.
  * Gestapelte Umgebungen ermöglichen das **Hinzufügen** von Werkzeugen zur primären Umgebung. Sie können eine Umgebung von Entwicklungstools an das Ende des Stacks anhängen, um sie aus dem REPL und Skripten verfügbar zu machen, jedoch nicht aus innerhalb von Paketen.

Auf hoher Ebene definiert jede Umgebung konzeptionell drei Karten: Wurzeln, Graph und Pfade. Bei der Auflösung der Bedeutung von `import X` werden die Wurzeln- und Graphkarten verwendet, um die Identität von `X` zu bestimmen, während die Pfadkarte verwendet wird, um den Quellcode von `X` zu lokalisieren. Die spezifischen Rollen der drei Karten sind:

  * **Wurzeln:** `name::Symbol` ⟶ `uuid::UUID`

    Eine Wurzelzuordnung der Umgebung weist Paketnamen UUIDs für alle obersten Abhängigkeiten zu, die der Umgebung für das Hauptprojekt zur Verfügung stehen (d.h. die, die in `Main` geladen werden können). Wenn Julia `import X` im Hauptprojekt begegnet, sucht es die Identität von `X` als `roots[:X]` auf.
  * **graph:** `context::UUID` ⟶ `name::Symbol` ⟶ `uuid::UUID`

    Ein Graph der Umgebung ist eine mehrstufige Karte, die für jede `context` UUID eine Zuordnung von Namen zu UUIDs bereitstellt, ähnlich der Wurzelkarte, aber spezifisch für diesen `context`. Wenn Julia `import X` im Code des Pakets sieht, dessen UUID `context` ist, sucht sie die Identität von `X` als `graph[context][:X]`. Dies bedeutet insbesondere, dass `import X` je nach `context` auf unterschiedliche Pakete verweisen kann.
  * **pfade:** `uuid::UUID` × `name::Symbol` ⟶ `pfad::String`

    Die Pfadkarte weist jedem Paket-UUID-Namen-Paar den Speicherort der Quell-Datei des Einstiegspunkts dieses Pakets zu. Nachdem die Identität von `X` in `import X` über Wurzeln oder Graph (je nachdem, ob es aus dem Hauptprojekt oder einer Abhängigkeit geladen wird) auf eine UUID aufgelöst wurde, bestimmt Julia, welche Datei geladen werden soll, um `X` zu erwerben, indem sie `paths[uuid,:X]` in der Umgebung nachschlägt. Das Einfügen dieser Datei sollte ein Modul mit dem Namen `X` definieren. Sobald dieses Paket geladen ist, wird jeder nachfolgende Import, der auf dasselbe `uuid` verweist, eine neue Bindung an das bereits geladene Paketmodul erstellen.

Jede Art von Umgebung definiert diese drei Karten unterschiedlich, wie in den folgenden Abschnitten detailliert beschrieben.

!!! note
    Um das Verständnis zu erleichtern, zeigen die Beispiele in diesem Kapitel vollständige Datenstrukturen für Wurzeln, Graphen und Pfade. Der Code zum Laden von Julias Paketen erstellt diese jedoch nicht explizit. Stattdessen berechnet er nur so viel von jeder Struktur, wie benötigt wird, um ein bestimmtes Paket zu laden.


### Project environments

Eine Projektumgebung wird durch ein Verzeichnis bestimmt, das eine Projektdatei namens `Project.toml` enthält, und optional eine Manifestdatei namens `Manifest.toml`. Diese Dateien können auch `JuliaProject.toml` und `JuliaManifest.toml` genannt werden, in diesem Fall werden `Project.toml` und `Manifest.toml` ignoriert. Dies ermöglicht die Koexistenz mit anderen Tools, die Dateien namens `Project.toml` und `Manifest.toml` als bedeutend betrachten. Für reine Julia-Projekte sind jedoch die Namen `Project.toml` und `Manifest.toml` bevorzugt. Ab Julia v1.10.8 wird jedoch `(Julia)Manifest-v{major}.{minor}.toml` als ein Format anerkannt, um eine bestimmte Julia-Version dazu zu bringen, eine spezifische Manifestdatei zu verwenden, d.h. im selben Ordner würde `Manifest-v1.11.toml` von v1.11 verwendet und `Manifest.toml` von jeder anderen Julia-Version.

Die Wurzeln, Grafiken und Pfadkarten einer Projektumgebung sind wie folgt definiert:

**Die Wurzelkarte** der Umgebung wird durch den Inhalt der Projektdatei bestimmt, insbesondere durch die obersten `name`- und `uuid`-Einträge sowie den Abschnitt `[deps]` (alle optional). Betrachten Sie die folgende Beispielprojektdatei für die hypothetische Anwendung `App`, wie zuvor beschrieben:

```toml
name = "App"
uuid = "8f986787-14fe-4607-ba5d-fbff2944afa9"

[deps]
Priv = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
Pub  = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
```

Diese Projektdatei impliziert die folgende Wurzelkarte, wenn sie durch ein Julia-Wörterbuch dargestellt wird:

```julia
roots = Dict(
    :App  => UUID("8f986787-14fe-4607-ba5d-fbff2944afa9"),
    :Priv => UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"),
    :Pub  => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
)
```

Gegeben dieser Roots-Karte wird im Code von `App` die Anweisung `import Priv` dazu führen, dass Julia `roots[:Priv]` nachschlägt, was `ba13f791-ae1d-465a-978b-69c3ad90f72b` ergibt, die UUID des `Priv`-Pakets, das in diesem Kontext geladen werden soll. Diese UUID identifiziert, welches `Priv`-Paket geladen und verwendet werden soll, wenn die Hauptanwendung `import Priv` auswertet.

**Der Abhängigkeitsgraph** einer Projektumgebung wird durch den Inhalt der Manifestdatei bestimmt, sofern vorhanden. Wenn keine Manifestdatei vorhanden ist, ist der Graph leer. Eine Manifestdatei enthält eine Strophe für jede direkte oder indirekte Abhängigkeit eines Projekts. Für jede Abhängigkeit listet die Datei die UUID des Pakets und einen Hash des Quellbaums oder einen expliziten Pfad zum Quellcode auf. Betrachten Sie die folgende Beispiel-Manifestdatei für `App`:

```toml
[[Priv]] # the private one
deps = ["Pub", "Zebra"]
uuid = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
path = "deps/Priv"

[[Priv]] # the public one
uuid = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
git-tree-sha1 = "1bf63d3be994fe83456a03b874b409cfd59a6373"
version = "0.1.5"

[[Pub]]
uuid = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
git-tree-sha1 = "9ebd50e2b0dd1e110e842df3b433cb5869b0dd38"
version = "2.1.4"

  [Pub.deps]
  Priv = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
  Zebra = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"

[[Zebra]]
uuid = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"
git-tree-sha1 = "e808e36a5d7173974b90a15a353b564f3494092f"
version = "3.4.2"
```

Diese Manifestdatei beschreibt ein mögliches vollständiges Abhängigkeitsdiagramm für das `App`-Projekt:

  * Es gibt zwei verschiedene Pakete mit dem Namen `Priv`, die die Anwendung verwendet. Es verwendet ein privates Paket, das eine Hauptabhängigkeit ist, und ein öffentliches, das eine indirekte Abhängigkeit über `Pub` ist. Diese werden durch ihre unterschiedlichen UUIDs unterschieden, und sie haben unterschiedliche Abhängigkeiten:

      * Das private `Priv` hängt von den Paketen `Pub` und `Zebra` ab.
      * Die öffentliche `Priv` hat keine Abhängigkeiten.
  * Die Anwendung hängt auch vom `Pub`-Paket ab, das wiederum vom öffentlichen `Priv` und dem gleichen `Zebra`-Paket abhängt, von dem das private `Priv`-Paket abhängt.

Dieser Abhängigkeitsgraph, der als Wörterbuch dargestellt ist, sieht so aus:

```julia
graph = Dict(
    # Priv – the private one:
    UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b") => Dict(
        :Pub   => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Priv – the public one:
    UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c") => Dict(),
    # Pub:
    UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1") => Dict(
        :Priv  => UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Zebra:
    UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62") => Dict(),
)
```

Gegebenen diese Abhängigkeit `graph`, wenn Julia `import Priv` im `Pub`-Paket sieht—das die UUID `c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1` hat—sucht es nach:

```julia
graph[UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1")][:Priv]
```

und erhält `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`, was darauf hinweist, dass im Kontext des `Pub`-Pakets `import Priv` auf das öffentliche `Priv`-Paket verweist, anstatt auf das private, von dem die App direkt abhängt. So kann der Name `Priv` in dem Hauptprojekt auf andere Pakete verweisen als in einem der Abhängigkeiten des Pakets, was doppelte Namen im Paket-Ökosystem ermöglicht.

Was passiert, wenn `import Zebra` im Hauptcode der `App` ausgewertet wird? Da `Zebra` nicht in der Projektdatei erscheint, wird der Import fehlschlagen, obwohl `Zebra` *im* Manifestfile erscheint. Darüber hinaus würde der Import von `Zebra`, wenn er im öffentlichen `Priv`-Paket erfolgt—dem mit der UUID `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`—auch fehlschlagen, da dieses `Priv`-Paket keine deklarierten Abhängigkeiten im Manifestfile hat und daher keine Pakete laden kann. Das `Zebra`-Paket kann nur von Paketen geladen werden, für die es als explizite Abhängigkeit im Manifestfile erscheint: dem `Pub`-Paket und einem der `Priv`-Pakete.

**Die Pfade-Karte** einer Projektumgebung wird aus der Manifestdatei extrahiert. Der Pfad eines Pakets `uuid` mit dem Namen `X` wird durch diese Regeln (in der Reihenfolge) bestimmt:

1. Wenn die Projektdatei im Verzeichnis mit `uuid` und dem Namen `X` übereinstimmt, dann entweder:

      * Es hat einen obersten `path`-Eintrag, dann wird `uuid` auf diesen Pfad abgebildet, der relativ zum Verzeichnis interpretiert wird, das die Projektdatei enthält.
      * Andernfalls wird `uuid` relativ zum Verzeichnis, das die Projektdatei enthält, auf `src/X.jl` abgebildet.
2. Wenn dies nicht der Fall ist und die Projektdatei eine entsprechende Manifestdatei hat und das Manifest eine Strophe enthält, die mit `uuid` übereinstimmt, dann:

      * Wenn es einen `path`-Eintrag gibt, verwenden Sie diesen Pfad (relativ zum Verzeichnis, das die Manifestdatei enthält).
      * Wenn es einen `git-tree-sha1`-Eintrag gibt, berechne eine deterministische Hash-Funktion von `uuid` und `git-tree-sha1`—nennen wir es `slug`—und suche in jedem Verzeichnis im globalen Array `DEPOT_PATH` von Julia nach einem Verzeichnis namens `packages/X/$slug`. Verwende das erste vorhandene Verzeichnis.

Wenn eines dieser Ergebnisse erfolgreich ist, wird der Pfad zum Einstiegspunkt des Quellcodes entweder dieses Ergebnis sein, der relative Pfad von diesem Ergebnis plus `src/X.jl`; andernfalls gibt es keine Pfadzuordnung für `uuid`. Beim Laden von `X`, wenn kein Quellcodepfad gefunden wird, schlägt die Suche fehl, und der Benutzer kann aufgefordert werden, die entsprechende Paketversion zu installieren oder andere Korrekturmaßnahmen zu ergreifen (z. B. `X` als Abhängigkeit zu deklarieren).

Im obigen Beispiel-Manifestdatei sucht Julia den Pfad des ersten `Priv`-Pakets—das mit der UUID `ba13f791-ae1d-465a-978b-69c3ad90f72b`—indem sie nach seinem Abschnitt in der Manifestdatei sucht, sieht, dass es einen `path`-Eintrag hat, schaut sich `deps/Priv` relativ zum `App`-Projektverzeichnis an—nehmen wir an, der `App`-Code befindet sich in `/home/me/projects/App`—stellt fest, dass `/home/me/projects/App/deps/Priv` existiert und lädt daher `Priv` von dort.

Wenn Julia hingegen das *andere* `Priv`-Paket lädt—das mit der UUID `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`—findet es seinen Abschnitt im Manifest, sieht, dass es keinen `path`-Eintrag hat, aber dass es einen `git-tree-sha1`-Eintrag gibt. Es berechnet dann den `slug` für dieses UUID/SHA-1-Paar, der `HDkrT` ist (die genauen Details dieser Berechnung sind nicht wichtig, aber sie ist konsistent und deterministisch). Das bedeutet, dass der Pfad zu diesem `Priv`-Paket `packages/Priv/HDkrT/src/Priv.jl` in einem der Paketdepots sein wird. Angenommen, der Inhalt von `DEPOT_PATH` ist `["/home/me/.julia", "/usr/local/julia"]`, dann wird Julia die folgenden Pfade überprüfen, um zu sehen, ob sie existieren:

1. `/home/me/.julia/packages/Priv/HDkrT`
2. `/usr/local/julia/packages/Priv/HDkrT`

Julia verwendet das erste dieser Elemente, das existiert, um zu versuchen, das öffentliche `Priv`-Paket aus der Datei `packages/Priv/HDKrT/src/Priv.jl` im Depot, wo es gefunden wurde, zu laden.

Hier ist eine Darstellung einer möglichen Pfadkarte für unsere Beispiel-`App`-Projektumgebung, wie im obigen Manifest für das Abhängigkeitsdiagramm angegeben, nachdem das lokale Dateisystem durchsucht wurde:

```julia
paths = Dict(
    # Priv – the private one:
    (UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"), :Priv) =>
        # relative entry-point inside `App` repo:
        "/home/me/projects/App/deps/Priv/src/Priv.jl",
    # Priv – the public one:
    (UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"), :Priv) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Priv/HDkr/src/Priv.jl",
    # Pub:
    (UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"), :Pub) =>
        # package installed in the user depot:
        "/home/me/.julia/packages/Pub/oKpw/src/Pub.jl",
    # Zebra:
    (UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"), :Zebra) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Zebra/me9k/src/Zebra.jl",
)
```

Diese Beispielkarte enthält drei verschiedene Arten von Paketstandorten (der erste und der dritte sind Teil des Standardladepfads):

1. Das private `Priv` Paket ist "[vendored](https://stackoverflow.com/a/35109534)" im `App` Repository.
2. Die öffentlichen `Priv`- und `Zebra`-Pakete befinden sich im Systemdepot, wo Pakete installiert und vom Systemadministrator verwaltet werden. Diese sind für alle Benutzer im System verfügbar.
3. Das `Pub`-Paket befindet sich im Benutzerdepot, wo die vom Benutzer installierten Pakete gespeichert sind. Diese sind nur für den Benutzer verfügbar, der sie installiert hat.

### Package directories

Paketverzeichnisse bieten eine einfachere Art von Umgebung, ohne die Möglichkeit, Namenskonflikte zu behandeln. In einem Paketverzeichnis ist die Menge der obersten Pakete die Menge der Unterverzeichnisse, die "wie" Pakete aussehen. Ein Paket `X` existiert in einem Paketverzeichnis, wenn das Verzeichnis eine der folgenden "Einstiegspunkt"-Dateien enthält:

  * `X.jl`
  * `X/src/X.jl`
  * `X.jl/src/X.jl`

Welche Abhängigkeiten ein Paket in einem Paketverzeichnis importieren kann, hängt davon ab, ob das Paket eine Projektdatei enthält:

  * Wenn es eine Projektdatei hat, kann es nur die Pakete importieren, die im Abschnitt `[deps]` der Projektdatei aufgeführt sind.
  * Wenn es keine Projektdatei hat, kann es jedes Top-Level-Paket importieren – d.h. die gleichen Pakete, die in `Main` oder dem REPL geladen werden können.

**Die Wurzelkarte** wird erstellt, indem der Inhalt des Paketverzeichnisses untersucht wird, um eine Liste aller vorhandenen Pakete zu generieren. Darüber hinaus wird jeder Eintragung eine UUID zugewiesen, wie folgt: Für ein gegebenes Paket, das im Ordner `X` gefunden wird...

1. Wenn `X/Project.toml` existiert und einen `uuid`-Eintrag hat, dann ist `uuid` dieser Wert.
2. Wenn `X/Project.toml` existiert, aber keinen UUID-Eintrag auf oberster Ebene hat, ist `uuid` eine Dummy-UUID, die durch Hashing des kanonischen (echten) Pfads zu `X/Project.toml` generiert wird.
3. Andernfalls (wenn `Project.toml` nicht existiert), ist `uuid` der All-Zero [nil UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier#Nil_UUID).

**Der Abhängigkeitsgraph** eines Projektverzeichnisses wird durch die Anwesenheit und den Inhalt von Projektdateien im Unterverzeichnis jedes Pakets bestimmt. Die Regeln sind:

  * Wenn ein Paketunterverzeichnis keine Projektdatei hat, wird es aus dem Graphen weggelassen und Importanweisungen in seinem Code werden als top-level behandelt, genau wie das Hauptprojekt und REPL.
  * Wenn ein Paketunterverzeichnis eine Projektdatei hat, dann ist der Grapheneintrag für seine UUID die `[deps]`-Karte der Projektdatei, die als leer betrachtet wird, wenn der Abschnitt fehlt.

Als Beispiel nehmen wir an, dass ein Paketverzeichnis die folgende Struktur und den folgenden Inhalt hat:

```
Aardvark/
    src/Aardvark.jl:
        import Bobcat
        import Cobra

Bobcat/
    Project.toml:
        [deps]
        Cobra = "4725e24d-f727-424b-bca0-c4307a3456fa"
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Bobcat.jl:
        import Cobra
        import Dingo

Cobra/
    Project.toml:
        uuid = "4725e24d-f727-424b-bca0-c4307a3456fa"
        [deps]
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Cobra.jl:
        import Dingo

Dingo/
    Project.toml:
        uuid = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Dingo.jl:
        # no imports
```

Hier ist eine entsprechende Wurzelstruktur, dargestellt als ein Wörterbuch:

```julia
roots = Dict(
    :Aardvark => UUID("00000000-0000-0000-0000-000000000000"), # no project file, nil UUID
    :Bobcat   => UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), # dummy UUID based on path
    :Cobra    => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), # UUID from project file
    :Dingo    => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), # UUID from project file
)
```

Hier ist die entsprechende Graphstruktur, dargestellt als ein Wörterbuch:

```julia
graph = Dict(
    # Bobcat:
    UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf") => Dict(
        :Cobra => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"),
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Cobra:
    UUID("4725e24d-f727-424b-bca0-c4307a3456fa") => Dict(
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Dingo:
    UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc") => Dict(),
)
```

Einige allgemeine Regeln zu beachten:

1. Ein Paket ohne eine Projektdatei kann von jeder obersten Abhängigkeit abhängen, und da jedes Paket in einem Paketverzeichnis auf der obersten Ebene verfügbar ist, kann es alle Pakete in der Umgebung importieren.
2. Ein Paket mit einer Projektdatei kann nicht von einem ohne Projektdatei abhängen, da Pakete mit Projektdateien nur Pakete im `graph` laden können und Pakete ohne Projektdateien im `graph` nicht erscheinen.
3. Ein Paket mit einer Projektdatei, aber ohne explizite UUID kann nur von Paketen ohne Projektdateien abhängig sein, da die Dummy-UUIDs, die diesen Paketen zugewiesen sind, streng intern sind.

Beobachten Sie die folgenden spezifischen Beispiele für diese Regeln in unserem Beispiel:

  * `Aardvark` kann auf jeden von `Bobcat`, `Cobra` oder `Dingo` importieren; es importiert `Bobcat` und `Cobra`.
  * `Bobcat` kann und importiert sowohl `Cobra` als auch `Dingo`, die beide Projektdateien mit UUIDs haben und im `[deps]`-Abschnitt von `Bobcat` als Abhängigkeiten deklariert sind.
  * `Bobcat` kann nicht von `Aardvark` abhängen, da `Aardvark` keine Projektdatei hat.
  * `Cobra` kann und importiert `Dingo`, das eine Projektdatei und UUID hat und im `[deps]`-Abschnitt von `Cobra` als Abhängigkeit deklariert ist.
  * `Cobra` kann nicht von `Aardvark` oder `Bobcat` abhängen, da keiner von beiden echte UUIDs hat.
  * `Dingo` kann nichts importieren, da es eine Projektdatei ohne einen `[deps]` Abschnitt hat.

**Die Pfade-Karte** in einem Paketverzeichnis ist einfach: Sie ordnet die Namen der Unterverzeichnisse ihren entsprechenden Einstiegspunkt-Pfaden zu. Mit anderen Worten, wenn der Pfad zu unserem Beispielprojektverzeichnis `/home/me/animals` ist, könnte die `paths`-Karte durch dieses Wörterbuch dargestellt werden:

```julia
paths = Dict(
    (UUID("00000000-0000-0000-0000-000000000000"), :Aardvark) =>
        "/home/me/AnimalPackages/Aardvark/src/Aardvark.jl",
    (UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), :Bobcat) =>
        "/home/me/AnimalPackages/Bobcat/src/Bobcat.jl",
    (UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), :Cobra) =>
        "/home/me/AnimalPackages/Cobra/src/Cobra.jl",
    (UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), :Dingo) =>
        "/home/me/AnimalPackages/Dingo/src/Dingo.jl",
)
```

Da alle Pakete in einer Paketverzeichnisumgebung definitionsgemäß Unterverzeichnisse mit den erwarteten Einstiegspunktdateien sind, haben ihre `paths`-Mapping-Einträge immer diese Form.

### Environment stacks

Die dritte und letzte Art von Umgebung ist eine, die andere Umgebungen kombiniert, indem mehrere von ihnen übereinandergelegt werden, wodurch die Pakete in jeder von ihnen in einer einzigen zusammengesetzten Umgebung verfügbar gemacht werden. Diese zusammengesetzten Umgebungen werden *Umgebungsstapel* genannt. Der globale `LOAD_PATH` in Julia definiert einen Umgebungsstapel—die Umgebung, in der der Julia-Prozess arbeitet. Wenn Sie möchten, dass Ihr Julia-Prozess nur Zugriff auf die Pakete in einem Projekt oder Verzeichnis hat, machen Sie es zum einzigen Eintrag in `LOAD_PATH`. Es ist jedoch oft sehr nützlich, Zugriff auf einige Ihrer Lieblingswerkzeuge zu haben—Standardbibliotheken, Profiler, Debugger, persönliche Dienstprogramme usw.—auch wenn sie keine Abhängigkeiten des Projekts sind, an dem Sie arbeiten. Indem Sie eine Umgebung, die diese Werkzeuge enthält, zum Ladepfad hinzufügen, haben Sie sofort Zugriff auf sie im Top-Level-Code, ohne sie zu Ihrem Projekt hinzufügen zu müssen.

Der Mechanismus zum Kombinieren der Wurzeln, Grafiken und Pfaddatenstrukturen der Komponenten eines Umgebungsstapels ist einfach: Sie werden als Wörterbücher zusammengeführt, wobei frühere Einträge bei Schlüsselkonflikten den späteren vorgezogen werden. Mit anderen Worten, wenn wir `stack = [env₁, env₂, …]` haben, dann haben wir:

```julia
roots = reduce(merge, reverse([roots₁, roots₂, …]))
graph = reduce(merge, reverse([graph₁, graph₂, …]))
paths = reduce(merge, reverse([paths₁, paths₂, …]))
```

Die indizierten Variablen `rootsᵢ`, `graphᵢ` und `pathsᵢ` entsprechen den indizierten Umgebungen `envᵢ`, die im `stack` enthalten sind. Das `reverse` ist vorhanden, da `merge` das letzte Argument gegenüber dem ersten bevorzugt, wenn es Kollisionen zwischen Schlüsseln in seinen Argumentdictionaries gibt. Es gibt ein paar bemerkenswerte Merkmale dieses Designs:

1. Die *primäre Umgebung*—d.h. die erste Umgebung in einem Stapel—ist treu in einer gestapelten Umgebung eingebettet. Der vollständige Abhängigkeitsgraph der ersten Umgebung in einem Stapel ist garantiert intakt in der gestapelten Umgebung enthalten, einschließlich der gleichen Versionen aller Abhängigkeiten.
2. Pakete in nicht primären Umgebungen können inkompatible Versionen ihrer Abhängigkeiten verwenden, selbst wenn ihre eigenen Umgebungen vollständig kompatibel sind. Dies kann passieren, wenn eine ihrer Abhängigkeiten von einer Version in einer früheren Umgebung im Stapel (entweder durch Graph oder Pfad, oder beides) überschattet wird.

Da die primäre Umgebung typischerweise die Umgebung eines Projekts ist, an dem Sie arbeiten, während die Umgebungen weiter oben im Stack zusätzliche Tools enthalten, ist dies der richtige Kompromiss: Es ist besser, Ihre Entwicklungstools zu brechen, aber das Projekt funktionsfähig zu halten. Wenn solche Inkompatibilitäten auftreten, möchten Sie in der Regel Ihre Entwicklungstools auf Versionen aktualisieren, die mit dem Hauptprojekt kompatibel sind.

### [Package Extensions](@id man-extensions)

Ein Paket "Erweiterung" ist ein Modul, das automatisch geladen wird, wenn eine bestimmte Menge anderer Pakete (seiner "Auslöser") in der aktuellen Julia-Sitzung geladen wird. Erweiterungen werden im Abschnitt `[extensions]` der Projektdatei definiert. Die Auslöser einer Erweiterung sind eine Teilmenge der Pakete, die im Abschnitt `[weakdeps]` (und möglicherweise, aber unüblich im Abschnitt `[deps]`) der Projektdatei aufgeführt sind. Diese Pakete können wie andere Pakete Kompatibilitätseinträge haben.

```toml
name = "MyPackage"

[compat]
ExtDep = "1.0"
OtherExtDep = "1.0"

[weakdeps]
ExtDep = "c9a23..." # uuid
OtherExtDep = "862e..." # uuid

[extensions]
BarExt = ["ExtDep", "OtherExtDep"]
FooExt = "ExtDep"
...
```

Die Schlüssel unter `extensions` sind die Namen der Erweiterungen. Sie werden geladen, wenn alle Pakete auf der rechten Seite (die Auslöser) dieser Erweiterung geladen sind. Wenn eine Erweiterung nur einen Auslöser hat, kann die Liste der Auslöser der Kürze halber einfach als Zeichenfolge geschrieben werden. Der Speicherort für den Einstiegspunkt der Erweiterung befindet sich entweder in `ext/FooExt.jl` oder `ext/FooExt/FooExt.jl` für die Erweiterung `FooExt`. Der Inhalt einer Erweiterung ist oft wie folgt strukturiert:

```
module FooExt

# Load main package and triggers
using MyPackage, ExtDep

# Extend functionality in main package with types from the triggers
MyPackage.func(x::ExtDep.SomeStruct) = ...

end
```

Wenn ein Paket mit Erweiterungen zu einer Umgebung hinzugefügt wird, werden die Abschnitte `weakdeps` und `extensions` in der Manifestdatei im Abschnitt für dieses Paket gespeichert. Die Regeln zur Abhängigkeitsprüfung für ein Paket sind die gleichen wie für sein "Elternteil", mit der Ausnahme, dass die aufgeführten Trigger ebenfalls als Abhängigkeiten betrachtet werden.

### [Package/Environment Preferences](@id preferences)

Präferenzen sind Wörterbücher von Metadaten, die das Verhalten von Paketen innerhalb einer Umgebung beeinflussen. Das Präferenzsystem unterstützt das Lesen von Präferenzen zur Compile-Zeit, was bedeutet, dass wir zur Zeit des Code-Ladens sicherstellen müssen, dass die von Julia ausgewählten Vorcompilierungsdateien mit denselben Präferenzen wie die aktuelle Umgebung erstellt wurden, bevor wir sie laden. Die öffentliche API zur Modifizierung von Präferenzen ist im [Preferences.jl](https://github.com/JuliaPackaging/Preferences.jl)-Paket enthalten. Präferenzen werden als TOML-Wörterbücher in einer `(Julia)LocalPreferences.toml`-Datei neben dem aktuell aktiven Projekt gespeichert. Wenn eine Präferenz "exportiert" wird, wird sie stattdessen in der `(Julia)Project.toml` gespeichert. Die Absicht ist es, gemeinsamen Projekten gemeinsame Präferenzen zu ermöglichen, während es den Benutzern selbst erlaubt wird, diese Präferenzen mit ihren eigenen Einstellungen in der LocalPreferences.toml-Datei zu überschreiben, die, wie der Name schon sagt, .gitignored werden sollte.

Präferenzen, die während der Kompilierung zugegriffen werden, werden automatisch als Kompilierungspräferenzen markiert, und jede Änderung, die an diesen Präferenzen aufgezeichnet wird, führt dazu, dass der Julia-Compiler alle zwischengespeicherten Vorcompilierungsdateien (`.ji` und entsprechende `.so`, `.dll` oder `.dylib`-Dateien) für dieses Modul neu kompiliert. Dies geschieht, indem der Hash aller Kompilierungspräferenzen während der Kompilierung serialisiert wird und dann dieser Hash mit der aktuellen Umgebung verglichen wird, wenn nach den richtigen Dateien zum Laden gesucht wird.

Präferenzen können mit depotweiten Standardeinstellungen festgelegt werden; wenn das Paket Foo in Ihrer globalen Umgebung installiert ist und es festgelegte Präferenzen hat, gelten diese Präferenzen, solange Ihre globale Umgebung Teil Ihres `LOAD_PATH` ist. Präferenzen in Umgebungen, die höher in der Umgebungsstapel stehen, werden von den näheren Einträgen im Ladepfad überschrieben, beginnend mit dem aktuell aktiven Projekt. Dies ermöglicht es, dass depotweite Präferenzstandards existieren, wobei aktive Projekte in der Lage sind, diese geerbten Präferenzen zu kombinieren oder sogar vollständig zu überschreiben. Siehe die Docstring für `Preferences.set_preferences!()` für die vollständigen Details, wie man Präferenzen festlegt, um das Zusammenführen zu erlauben oder zu verbieten.

## Conclusion

Federierte Paketverwaltung und präzise Software-Reproduzierbarkeit sind schwierige, aber lohnenswerte Ziele in einem Paket-System. In Kombination führen diese Ziele zu einem komplexeren Paketlade-Mechanismus als die meisten dynamischen Sprachen haben, aber sie bieten auch Skalierbarkeit und Reproduzierbarkeit, die häufiger mit statischen Sprachen assoziiert werden. Typischerweise sollten Julia-Nutzer in der Lage sein, den integrierten Paketmanager zu verwenden, um ihre Projekte zu verwalten, ohne ein präzises Verständnis dieser Interaktionen zu benötigen. Ein Aufruf von `Pkg.add("X")` wird die entsprechenden Projekt- und Manifestdateien hinzufügen, die über `Pkg.activate("Y")` ausgewählt werden, sodass ein zukünftiger Aufruf von `import X` `X` ohne weiteres Nachdenken lädt.
