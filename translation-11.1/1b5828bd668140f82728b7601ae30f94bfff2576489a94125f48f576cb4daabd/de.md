# Handling Operating System Variation

Beim Schreiben von plattformübergreifenden Anwendungen oder Bibliotheken ist es oft notwendig, Unterschiede zwischen Betriebssystemen zu berücksichtigen. Die Variable `Sys.KERNEL` kann verwendet werden, um solche Fälle zu behandeln. Es gibt mehrere Funktionen im `Sys`-Modul, die dies erleichtern sollen, wie `isunix`, `islinux`, `isapple`, `isbsd`, `isfreebsd` und `iswindows`. Diese können wie folgt verwendet werden:

```julia
if Sys.iswindows()
    windows_specific_thing(a)
end
```

Beachten Sie, dass `islinux`, `isapple` und `isfreebsd` gegenseitig ausschließende Teilmengen von `isunix` sind. Darüber hinaus gibt es ein Makro `@static`, das es ermöglicht, diese Funktionen zu verwenden, um ungültigen Code bedingt auszublenden, wie in den folgenden Beispielen gezeigt.

Einfache Blöcke:

```
ccall((@static Sys.iswindows() ? :_fopen : :fopen), ...)
```

Komplexe Blöcke:

```julia
@static if Sys.islinux()
    linux_specific_thing(a)
elseif Sys.isapple()
    apple_specific_thing(a)
else
    generic_thing(a)
end
```

Beim Verschachteln von Bedingungen muss `@static` für jede Ebene wiederholt werden (Klammern sind optional, aber zur besseren Lesbarkeit empfohlen):

```julia
@static Sys.iswindows() ? :a : (@static Sys.isapple() ? :b : :c)
```
