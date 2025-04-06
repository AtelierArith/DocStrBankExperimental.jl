```
@time_imports
```

Ein Makro, um einen Ausdruck auszuführen und einen Bericht über die gesamte Zeit zu erstellen, die für das Importieren von Paketen und deren Abhängigkeiten aufgewendet wurde. Jegliche Kompilierungszeit wird als Prozentsatz angegeben, sowie wie viel davon eine Rekompilierung war, falls vorhanden.

Pro Paket oder Paket-Erweiterung wird eine Zeile ausgegeben. Die angezeigte Dauer ist die Zeit, die benötigt wird, um dieses Paket selbst zu importieren, ohne die Zeit für das Laden seiner Abhängigkeiten einzubeziehen.

In Julia 1.9+ werden [Paket-Erweiterungen](@ref man-extensions) als Parent → Extension angezeigt.

!!! Hinweis     Während des Ladeprozesses importiert ein Paket nacheinander alle seine Abhängigkeiten, nicht nur seine direkten Abhängigkeiten.

```julia-repl
julia> @time_imports using CSV
     50.7 ms  Parsers 17.52% Kompilierungszeit
      0.2 ms  DataValueInterfaces
      1.6 ms  DataAPI
      0.1 ms  IteratorInterfaceExtensions
      0.1 ms  TableTraits
     17.5 ms  Tables
     26.8 ms  PooledArrays
    193.7 ms  SentinelArrays 75.12% Kompilierungszeit
      8.6 ms  InlineStrings
     20.3 ms  WeakRefStrings
      2.0 ms  TranscodingStreams
      1.4 ms  Zlib_jll
      1.8 ms  CodecZlib
      0.8 ms  Compat
     13.1 ms  FilePathsBase 28.39% Kompilierungszeit
   1681.2 ms  CSV 92.40% Kompilierungszeit
```

!!! kompat "Julia 1.8"
    Dieses Makro erfordert mindestens Julia 1.8

