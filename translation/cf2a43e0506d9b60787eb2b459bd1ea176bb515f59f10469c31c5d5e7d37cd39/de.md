```
DateTime
```

`DateTime` repräsentiert einen Zeitpunkt gemäß dem proleptischen Gregorianischen Kalender. Die feinste Auflösung der Zeit ist Millisekunde (d.h. Mikrosekunden oder Nanosekunden können von diesem Typ nicht dargestellt werden). Der Typ unterstützt Festkommaarithmetik und ist daher anfällig für Unterlauf (und Überlauf). Eine bemerkenswerte Folge ist das Runden beim Hinzufügen einer `Microsecond` oder einer `Nanosecond`:

```jldoctest
julia> dt = DateTime(2023, 8, 19, 17, 45, 32, 900)
2023-08-19T17:45:32.900

julia> dt + Millisecond(1)
2023-08-19T17:45:32.901

julia> dt + Microsecond(1000) # 1000us == 1ms
2023-08-19T17:45:32.901

julia> dt + Microsecond(999) # 999us gerundet auf 1000us
2023-08-19T17:45:32.901

julia> dt + Microsecond(1499) # 1499 gerundet auf 1000us
2023-08-19T17:45:32.901
```
