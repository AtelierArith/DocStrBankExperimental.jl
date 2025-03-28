```
unsafe_wrap(Array, pointer::Ptr{T}, dims; own = false)
```

Wickeln Sie ein Julia `Array`-Objekt um die Daten an der Adresse, die durch `pointer` angegeben ist, ohne eine Kopie zu erstellen. Der Zeiger-Elementtyp `T` bestimmt den Array-Elementtyp. `dims` ist entweder eine Ganzzahl (für ein 1d-Array) oder ein Tupel der Array-Dimensionen. `own` gibt optional an, ob Julia das Eigentum an dem Speicher übernehmen soll, indem `free` auf den Zeiger aufgerufen wird, wenn das Array nicht mehr referenziert wird.

Diese Funktion ist als "unsicher" gekennzeichnet, da sie abstürzt, wenn `pointer` keine gültige Speicheradresse für Daten der angeforderten Länge ist. Im Gegensatz zu [`unsafe_load`](@ref) und [`unsafe_store!`](@ref) ist der Programmierer auch dafür verantwortlich, sicherzustellen, dass auf die zugrunde liegenden Daten nicht über zwei Arrays mit unterschiedlichem Elementtyp zugegriffen wird, ähnlich der strengen Aliasregel in C.
