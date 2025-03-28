```
PipeBuffer(data::AbstractVector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

Ein [`IOBuffer`](@ref), der das Lesen ermöglicht und Schreibvorgänge durch Anhängen durchführt. Suchen und Truncieren werden nicht unterstützt. Siehe [`IOBuffer`](@ref) für die verfügbaren Konstruktoren. Wenn `data` angegeben ist, wird ein `PipeBuffer` erstellt, um auf einen Datenvektor zu arbeiten, wobei optional eine Größe angegeben werden kann, über die das zugrunde liegende `Array` nicht vergrößert werden darf.
