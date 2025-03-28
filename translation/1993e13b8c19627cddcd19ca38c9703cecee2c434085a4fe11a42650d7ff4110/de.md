```
SamplerTrivial(x)
```

Erstellen Sie einen Sampler, der einfach den gegebenen Wert `x` umschließt. Dies ist der standardmäßige Rückfall für Werte. Der `eltype` dieses Samplers ist gleich `eltype(x)`.

Der empfohlene Anwendungsfall ist das Sampling von Werten ohne vorab berechnete Daten.
