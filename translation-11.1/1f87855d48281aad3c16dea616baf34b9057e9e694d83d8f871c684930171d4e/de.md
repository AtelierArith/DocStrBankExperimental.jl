```
IndexStyle(A)
IndexStyle(typeof(A))
```

`IndexStyle` gibt den "nativen Indexierungsstil" für das Array `A` an. Wenn Sie einen neuen [`AbstractArray`](@ref) Typ definieren, können Sie wählen, ob Sie entweder die lineare Indexierung (mit [`IndexLinear`](@ref)) oder die kartesische Indexierung implementieren möchten. Wenn Sie sich entscheiden, nur die lineare Indexierung zu implementieren, müssen Sie dieses Merkmal für Ihren Array-Typ festlegen:

```
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

Der Standardwert ist [`IndexCartesian()`](@ref).

Julias interne Indexierungsmechanismen werden automatisch (und unsichtbar) alle Indexierungsoperationen in den bevorzugten Stil umrechnen. Dies ermöglicht es Benutzern, auf Elemente Ihres Arrays mit jedem Indexierungsstil zuzugreifen, selbst wenn keine expliziten Methoden bereitgestellt wurden.

Wenn Sie beide Indexierungsstile für Ihr `AbstractArray` definieren, kann dieses Merkmal verwendet werden, um den leistungsfähigsten Indexierungsstil auszuwählen. Einige Methoden überprüfen dieses Merkmal bei ihren Eingaben und leiten je nach dem effizientesten Zugriffsmodus an unterschiedliche Algorithmen weiter. Insbesondere erstellt [`eachindex`](@ref) einen Iterator, dessen Typ von der Einstellung dieses Merkmals abhängt.
