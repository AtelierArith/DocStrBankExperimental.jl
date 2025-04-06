```
GC.safepoint()
```

Fügt einen Punkt im Programm ein, an dem die Garbage Collection ausgeführt werden kann. Dies kann in seltenen Fällen in mehrthreadigen Programmen nützlich sein, in denen einige Threads Speicher zuweisen (und daher möglicherweise GC ausführen müssen), während andere Threads nur einfache Operationen durchführen (keine Zuweisung, Aufgabenwechsel oder I/O). Das periodische Aufrufen dieser Funktion in nicht zuweisenden Threads ermöglicht es der Garbage Collection, ausgeführt zu werden.

!!! compat "Julia 1.4"
    Diese Funktion ist seit Julia 1.4 verfügbar.

