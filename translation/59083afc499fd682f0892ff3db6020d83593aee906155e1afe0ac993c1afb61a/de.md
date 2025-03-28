```
TaskLocalRNG
```

Der `TaskLocalRNG` hat einen Zustand, der lokal zu seiner Aufgabe ist, nicht zu seinem Thread. Er wird bei der Erstellung der Aufgabe mit dem Zustand seiner übergeordneten Aufgabe initialisiert, jedoch ohne den Zustand des RNG der übergeordneten Aufgabe voranzutreiben.

Ein Vorteil des `TaskLocalRNG` ist, dass er ziemlich schnell ist und reproduzierbare multithreaded Simulationen ermöglicht (abgesehen von Wettlaufbedingungen), unabhängig von den Entscheidungen des Planers. Solange die Anzahl der Threads nicht zur Entscheidungsfindung bei der Erstellung von Aufgaben verwendet wird, sind die Simulationsergebnisse auch unabhängig von der Anzahl der verfügbaren Threads / CPUs. Der Zufallsstrom sollte nicht von Hardware-Spezifika abhängen, bis hin zur Endianness und möglicherweise der Wortgröße.

Die Verwendung oder das Seed des RNG einer anderen Aufgabe als der von `current_task()` zurückgegebenen ist undefiniertes Verhalten: Es wird die meiste Zeit funktionieren und kann manchmal stillschweigend fehlschlagen.

Beim Seed von `TaskLocalRNG()` mit [`seed!`](@ref) kann der übergebene Seed, falls vorhanden, jede ganze Zahl sein.

!!! compat "Julia 1.11"
    Das Seed von `TaskLocalRNG()` mit einem negativen ganzzahligen Seed erfordert mindestens Julia 1.11.


!!! compat "Julia 1.10"
    Die Erstellung von Aufgaben führt seit Julia 1.10 nicht mehr zur Voranstellung des RNG-Zustands der übergeordneten Aufgabe.

