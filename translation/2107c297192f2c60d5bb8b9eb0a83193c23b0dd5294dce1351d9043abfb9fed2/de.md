# Parallel Computing

Julia unterstützt diese vier Kategorien der nebenläufigen und parallelen Programmierung:

1. **Asynchrone "Aufgaben", oder Koroutinen**:

    Julia-Aufgaben ermöglichen das Aussetzen und Fortsetzen von Berechnungen für I/O, Ereignisbehandlung, Produzenten-Verbraucher-Prozesse und ähnliche Muster. Aufgaben können durch Operationen wie [`wait`](@ref) und [`fetch`](@ref) synchronisiert werden und über [`Channel`](@ref)s kommunizieren. Während sie streng genommen keine parallele Berechnung für sich sind, ermöglicht Julia das Planen von [`Task`](@ref)s auf mehreren Threads.
2. **Multithreading**:

    Julias [multi-threading](@ref man-multithreading) bietet die Möglichkeit, Aufgaben gleichzeitig auf mehr als einem Thread oder CPU-Kern zu planen und dabei den Speicher zu teilen. Dies ist in der Regel der einfachste Weg, um Parallelität auf einem PC oder auf einem einzelnen großen Multi-Core-Server zu erreichen. Julias Multi-Threading ist komponierbar. Wenn eine multi-threaded Funktion eine andere multi-threaded Funktion aufruft, wird Julia alle Threads global auf verfügbaren Ressourcen planen, ohne eine Überbuchung vorzunehmen.
3. **Verteiltes Rechnen**:

    Verteiltes Rechnen führt mehrere Julia-Prozesse mit separaten Speicherbereichen aus. Diese können auf demselben Computer oder auf mehreren Computern sein. Die [`Distributed`](@ref man-distributed) Standardbibliothek bietet die Möglichkeit zur Remote-Ausführung einer Julia-Funktion. Mit diesem grundlegenden Baustein ist es möglich, viele verschiedene Arten von Abstraktionen für verteiltes Rechnen zu erstellen. Pakete wie [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) sind ein Beispiel für eine solche Abstraktion. Auf der anderen Seite bieten Pakete wie [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) und [`Elemental.jl`](https://github.com/JuliaParallel/Elemental.jl) Zugang zum bestehenden MPI-Ökosystem von Bibliotheken.
4. **GPU-Computing**:

    Der Julia-GPU-Compiler bietet die Möglichkeit, Julia-Code nativ auf GPUs auszuführen. Es gibt ein reichhaltiges Ökosystem von Julia-Paketen, die auf GPUs abzielen. Die [JuliaGPU.org](https://juliagpu.org)-Website bietet eine Liste von Funktionen, unterstützten GPUs, verwandten Paketen und Dokumentationen.
