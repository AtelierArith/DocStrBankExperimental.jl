```
@time_imports
```

Une macro pour exécuter une expression et produire un rapport de tout le temps passé à importer des packages et leurs dépendances. Tout le temps de compilation sera rapporté en pourcentage, ainsi que la part de recompilation, le cas échéant.

Une ligne est imprimée par package ou extension de package. La durée affichée est le temps pour importer ce package lui-même, sans inclure le temps pour charger ses dépendances.

Sur Julia 1.9+ [package extensions](@ref man-extensions) apparaîtra comme Parent → Extension.

!!! note
    Pendant le processus de chargement, un package importe séquentiellement toutes ses dépendances, pas seulement ses dépendances directes.


```julia-repl
julia> @time_imports using CSV
     50.7 ms  Parsers 17.52% temps de compilation
      0.2 ms  DataValueInterfaces
      1.6 ms  DataAPI
      0.1 ms  IteratorInterfaceExtensions
      0.1 ms  TableTraits
     17.5 ms  Tables
     26.8 ms  PooledArrays
    193.7 ms  SentinelArrays 75.12% temps de compilation
      8.6 ms  InlineStrings
     20.3 ms  WeakRefStrings
      2.0 ms  TranscodingStreams
      1.4 ms  Zlib_jll
      1.8 ms  CodecZlib
      0.8 ms  Compat
     13.1 ms  FilePathsBase 28.39% temps de compilation
   1681.2 ms  CSV 92.40% temps de compilation
```

!!! compat "Julia 1.8"
    Cette macro nécessite au moins Julia 1.8

