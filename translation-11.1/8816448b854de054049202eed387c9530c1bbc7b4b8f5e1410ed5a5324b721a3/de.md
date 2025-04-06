```
randjump(r::MersenneTwister, steps::Integer) -> MersenneTwister
```

Erstellt ein initialisiertes `MersenneTwister`-Objekt, dessen Zustand um `steps` Schritte vorwärts bewegt wird (ohne Zahlen zu generieren) von `r`. Ein solcher Schritt entspricht der Generierung von zwei `Float64`-Zahlen. Für jeden unterschiedlichen Wert von `steps` muss intern ein großes Polynom generiert werden. Eines ist bereits für `steps=big(10)^20` vorab berechnet.
