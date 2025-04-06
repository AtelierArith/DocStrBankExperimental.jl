```
primitiver Typ
```

`primitiver Typ` deklariert einen konkreten Typ, dessen Daten nur aus einer Reihe von Bits bestehen. Klassische Beispiele für primitive Typen sind Ganzzahlen und Fließkommawerte. Einige Beispiele für eingebaute primitive Typdeklarationen:

```julia
primitiver Typ Char 32 end
primitiver Typ Bool <: Integer 8 end
```

Die Zahl nach dem Namen gibt an, wie viele Bits Speicher der Typ benötigt. Derzeit werden nur Größen unterstützt, die Vielfache von 8 Bits sind. Die [`Bool`](@ref) Deklaration zeigt, wie ein primitiver Typ optional als Untertyp eines bestimmten Supertyps deklariert werden kann.
