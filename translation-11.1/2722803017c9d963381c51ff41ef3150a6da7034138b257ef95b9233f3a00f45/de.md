# Ahead of Time Compilation

Dieses Dokument beschreibt das Design und die Struktur des Ahead-of-Time (AOT) Kompilierungssystems in Julia. Dieses System wird verwendet, wenn Systembilder und Paketbilder generiert werden. Ein Großteil der hier beschriebenen Implementierung befindet sich in `aotcompile.cpp`, `staticdata.c` und `processor.cpp`.

## Introduction

Obwohl Julia normalerweise Code just-in-time (JIT) kompiliert, ist es möglich, Code im Voraus zu kompilieren und den resultierenden Code in einer Datei zu speichern. Dies kann aus mehreren Gründen nützlich sein:

1. Um die Zeit zu reduzieren, die benötigt wird, um einen Julia-Prozess zu starten.
2. Um die Zeit zu reduzieren, die im JIT-Compiler anstelle der Ausführung von Code verbracht wird (Zeit bis zur ersten Ausführung, TTFX).
3. Um die Menge an Speicher zu reduzieren, die vom JIT-Compiler verwendet wird.

## High-Level Overview

Die folgenden Beschreibungen sind ein Snapshot der aktuellen Implementierungsdetails des End-to-End-Pipelines, die intern abläuft, wenn der Benutzer ein neues AOT-Modul kompiliert, wie es geschieht, wenn er `using Foo` eingibt. Diese Details werden sich im Laufe der Zeit wahrscheinlich ändern, während wir bessere Möglichkeiten zur Handhabung implementieren, sodass die aktuellen Implementierungen möglicherweise nicht genau mit dem Datenfluss und den Funktionen übereinstimmen, die unten beschrieben sind.

### Compiling Code Images

Zunächst müssen die Methoden, die in nativen Code kompiliert werden müssen, identifiziert werden. Dies kann nur durch die tatsächliche Ausführung des zu kompilierenden Codes erfolgen, da die Menge der Methoden, die kompiliert werden müssen, von den Typen der an die Methoden übergebenen Argumente abhängt, und Methodenaufrufe mit bestimmten Kombinationen von Typen möglicherweise erst zur Laufzeit bekannt sind. Während dieses Prozesses werden die genauen Methoden, die der Compiler sieht, für die spätere Kompilierung verfolgt, was eine Kompilierungstrace erzeugt.

!!! note
    Derzeit führt Julia bei der Kompilierung von Bildern die Trace-Generierung in einem anderen Prozess aus als den Prozess, der die AOT-Kompilierung durchführt. Dies kann Auswirkungen haben, wenn man versucht, einen Debugger während der Vorabkompilierung zu verwenden. Der beste Weg, die Vorabkompilierung mit einem Debugger zu debuggen, besteht darin, den rr-Debugger zu verwenden, den gesamten Prozessbaum aufzuzeichnen, `rr ps` zu verwenden, um den relevanten fehlgeschlagenen Prozess zu identifizieren, und dann `rr replay -p PID` zu verwenden, um nur den fehlgeschlagenen Prozess erneut abzuspielen.


Sobald die zu kompilierenden Methoden identifiziert wurden, werden sie an die Funktion `jl_create_system_image` übergeben. Diese Funktion richtet eine Reihe von Datenstrukturen ein, die beim Serialisieren von nativen Code in eine Datei verwendet werden, und ruft dann `jl_create_native` mit dem Array von Methoden auf. `jl_create_native` führt die Codegenerierung für die Methoden durch und erzeugt ein oder mehrere LLVM-Module. `jl_create_system_image` zeichnet dann einige nützliche Informationen darüber auf, was die Codegenerierung aus dem Modul(en) produziert hat.

Die Module werden dann an `jl_dump_native` übergeben, zusammen mit den Informationen, die von `jl_create_system_image` aufgezeichnet wurden. `jl_dump_native` enthält den Code, der erforderlich ist, um die Module in Bitcode, Objekt- oder Assemblierungsdateien zu serialisieren, abhängig von den über die Befehlszeilenoptionen an Julia übergebenen Optionen. Der serialisierte Code und die Informationen werden dann als Archiv in eine Datei geschrieben.

Der letzte Schritt besteht darin, einen System-Linker auf die Objektdateien im Archiv auszuführen, das von `jl_dump_native` erzeugt wurde. Sobald dieser Schritt abgeschlossen ist, wird eine Shared Library mit dem kompilierten Code erstellt.

### Loading Code Images

Beim Laden eines Codebildes wird die von dem Linker erzeugte gemeinsame Bibliothek in den Speicher geladen. Die Systembilddaten werden dann aus der gemeinsamen Bibliothek geladen. Diese Daten enthalten Informationen über die Typen, Methoden und Codeinstanzen, die in die gemeinsame Bibliothek kompiliert wurden. Diese Daten werden verwendet, um den Zustand der Laufzeit wiederherzustellen, wie er war, als das Codebild kompiliert wurde.

Wenn das Codebild mit Mehrversionierung kompiliert wurde, wählt der Loader die geeignete Version jeder Funktion basierend auf den verfügbaren CPU-Funktionen des aktuellen Computers aus.

Für Systembilder, da kein anderer Code geladen wurde, ist der Zustand der Laufzeit jetzt derselbe wie beim Kompilieren des Codebildes. Bei Paketbildern kann sich die Umgebung im Vergleich zum Zeitpunkt der Kompilierung des Codes geändert haben, sodass jede Methode gegen die globale Methodentabelle überprüft werden muss, um festzustellen, ob sie weiterhin gültiger Code ist.

## Compiling Methods

### Tracing Compiled Methods

Julia hat ein Befehlszeilen-Flag, um alle Methoden aufzuzeichnen, die vom JIT-Compiler kompiliert werden, `--trace-compile=filename`. Wenn eine Funktion kompiliert wird und dieses Flag einen Dateinamen hat, wird Julia eine Precompile-Anweisung in diese Datei mit der Methode und den Argumenttypen, mit denen sie aufgerufen wurde, ausgeben. Dies erzeugt daher ein Precompile-Skript, das später im AOT-Kompilierungsprozess verwendet werden kann. Das [PrecompileTools](https://julialang.github.io/PrecompileTools.jl/stable/)-Paket verfügt über Werkzeuge, die es Paketentwicklern erleichtern können, diese Funktionalität zu nutzen.

### `jl_create_system_image`

`jl_create_system_image` speichert alle Julia-spezifischen Metadaten, die notwendig sind, um den Zustand der Laufzeit später wiederherzustellen. Dazu gehören Daten wie Codeinstanzen, Methodeninstanzen, Methodentabellen und Typinformationen. Diese Funktion richtet auch die Datenstrukturen ein, die notwendig sind, um den nativen Code in eine Datei zu serialisieren. Schließlich ruft sie `jl_create_native` auf, um ein oder mehrere LLVM-Module zu erstellen, die den nativen Code für die übergebenen Methoden enthalten. `jl_create_native` ist verantwortlich für die Ausführung der Codegenerierung für die übergebenen Methoden.

### `jl_dump_native`

`jl_dump_native` ist verantwortlich für die Serialisierung des LLVM-Moduls, das den nativen Code enthält, in eine Datei. Neben dem Modul wird die vom `jl_create_system_image` erzeugte Systembilddaten als globale Variable kompiliert. Die Ausgabe dieser Methode sind Bitcode-, Objekt- und/oder Assemblierungsarchive, die den Code und die Systembilddaten enthalten.

`jl_dump_native` ist typischerweise einer der größeren Zeitfresser beim Erzeugen von nativen Code, wobei ein Großteil der Zeit mit der Optimierung von LLVM IR und der Erzeugung von Maschinencode verbracht wird. Daher ist diese Funktion in der Lage, die Schritte der Optimierung und der Maschinencodeerzeugung zu multithreaden. Dieses Multithreading ist auf die Größe des Moduls parametrisiert, kann jedoch explizit überschrieben werden, indem die Umgebungsvariable [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS) gesetzt wird. Die standardmäßige maximale Anzahl von Threads beträgt die Hälfte der verfügbaren Threads, aber eine niedrigere Einstellung kann den Spitzenverbrauch von Arbeitsspeicher während der Kompilierung reduzieren.

`jl_dump_native` kann auch nativen Code erzeugen, der für mehrere Architekturen optimiert ist, wenn er mit dem Julia-Loader integriert ist. Dies wird ausgelöst, indem die Umgebungsvariable [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) gesetzt wird und durch den Multiversionierungsschritt in der Optimierungspipeline vermittelt wird. Um dies mit Multithreading zu ermöglichen, wird ein Annotationsschritt hinzugefügt, bevor das Modul in Untermodule aufgeteilt wird, die in ihren eigenen Threads ausgegeben werden, und dieser Annotationsschritt verwendet Informationen, die im gesamten Modul verfügbar sind, um zu entscheiden, welche Funktionen für verschiedene Architekturen geklont werden. Sobald die Annotation erfolgt ist, können einzelne Threads Code für verschiedene Architekturen parallel ausgeben, in dem Wissen, dass ein anderes Untermodul garantiert die notwendigen Funktionen erzeugt, die von einer geklonten Funktion aufgerufen werden.

Einige andere Metadaten darüber, wie das Modul serialisiert wurde, sind ebenfalls im Archiv gespeichert, wie die Anzahl der Threads, die zur Serialisierung des Moduls verwendet wurden, und die Anzahl der kompilierten Funktionen.

### Static Linking

Der letzte Schritt im AOT-Kompilierungsprozess besteht darin, einen Linker auf die Objektdateien im Archiv auszuführen, das von `jl_dump_native` erzeugt wurde. Dies erzeugt eine Shared Library, die den kompilierten Code enthält. Diese Shared Library kann dann von Julia geladen werden, um den Zustand der Laufzeit wiederherzustellen. Bei der Kompilierung eines System-Images wird der native Linker, der von einem C-Compiler verwendet wird, verwendet, um die endgültige Shared Library zu erzeugen. Für Paket-Images wird der LLVM-Linker LLD verwendet, um eine konsistentere Linking-Schnittstelle bereitzustellen.

## Loading Code Images

### Loading the Shared Library

Der erste Schritt beim Laden eines Codebildes besteht darin, die vom Linker erzeugte Shared Library zu laden. Dies geschieht durch den Aufruf von `jl_dlopen` mit dem Pfad zur Shared Library. Diese Funktion ist verantwortlich für das Laden der Shared Library und das Auflösen aller Symbole in der Bibliothek.

### Loading Native Code

Der Loader muss zunächst feststellen, ob der kompilierte native Code für die Architektur gültig ist, auf der der Loader ausgeführt wird. Dies ist notwendig, um die Ausführung von Anweisungen zu vermeiden, die ältere CPUs nicht erkennen. Dies geschieht, indem die verfügbaren CPU-Funktionen auf der aktuellen Maschine mit den CPU-Funktionen verglichen werden, für die der Code kompiliert wurde. Wenn die Mehrversionierung aktiviert ist, wählt der Loader die geeignete Version jeder Funktion basierend auf den verfügbaren CPU-Funktionen der aktuellen Maschine aus. Wenn keine der mehrversionierten Funktionalitäten vorhanden ist, wird der Loader einen Fehler auslösen.

Ein Teil des Multiversionierungsdurchlaufs erstellt eine Anzahl globaler Arrays aller Funktionen im Modul. Wenn dieser Prozess multithreaded ist, wird ein Array von Arrays erstellt, das vom Loader in ein großes Array mit all den Funktionen reorganisiert wird, die für diese Architektur kompiliert wurden. Ein ähnlicher Prozess tritt für die globalen Variablen im Modul auf.

### Setting Up Julia State

Der Loader verwendet dann die globalen Variablen und Funktionen, die durch das Laden von nativen Code erzeugt wurden, um die Kern-Datenstrukturen der Julia-Laufzeit im aktuellen Prozess einzurichten. Diese Einrichtung umfasst das Hinzufügen von Typen und Methoden zur Julia-Laufzeit und das Bereitstellen des zwischengespeicherten nativen Codes zur Verwendung durch andere Julia-Funktionen und den Interpreter. Für Paketbilder muss jede Methode validiert werden, da der Zustand der globalen Methodentabelle mit dem Zustand übereinstimmen muss, für den das Paketbild kompiliert wurde. Insbesondere, wenn zur Ladezeit ein anderer Satz von Methoden existiert als zur Kompilierzeit des Paketbildes, muss die Methode ungültig gemacht und bei der ersten Verwendung neu kompiliert werden. Dies ist notwendig, um sicherzustellen, dass die Ausführungssemantik gleich bleibt, unabhängig davon, ob ein Paket vorcompiliert wurde oder ob der Code direkt ausgeführt wurde. Systembilder müssen diese Validierung nicht durchführen, da die globale Methodentabelle zur Ladezeit leer ist. Daher haben Systembilder schnellere Ladezeiten als Paketbilder.
