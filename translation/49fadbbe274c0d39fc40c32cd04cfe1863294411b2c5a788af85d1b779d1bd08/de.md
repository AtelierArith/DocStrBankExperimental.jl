```
Base.Pairs(values, keys) <: AbstractDict{eltype(keys), eltype(values)}
```

Transformiert einen indexierbaren Container in eine Dictionary-Ansicht der gleichen Daten. Die Modifizierung des Schlüsselraums der zugrunde liegenden Daten kann dieses Objekt ungültig machen.
