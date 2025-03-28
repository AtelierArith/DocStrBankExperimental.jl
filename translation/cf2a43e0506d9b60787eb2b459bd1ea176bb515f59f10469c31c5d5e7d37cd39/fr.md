```
DateTime
```

`DateTime` représente un point dans le temps selon le calendrier grégorien proleptique. La plus fine résolution du temps est la milliseconde (c'est-à-dire que les microsecondes ou les nanosecondes ne peuvent pas être représentées par ce type). Le type prend en charge l'arithmétique à virgule fixe, et est donc sujet à des sous-dépassements (et des dépassements). Une conséquence notable est l'arrondi lors de l'ajout d'une `Microseconde` ou d'une `Nanoseconde` :

```jldoctest
julia> dt = DateTime(2023, 8, 19, 17, 45, 32, 900)
2023-08-19T17:45:32.900

julia> dt + Millisecond(1)
2023-08-19T17:45:32.901

julia> dt + Microsecond(1000) # 1000us == 1ms
2023-08-19T17:45:32.901

julia> dt + Microsecond(999) # 999us arrondi à 1000us
2023-08-19T17:45:32.901

julia> dt + Microsecond(1499) # 1499 arrondi à 1000us
2023-08-19T17:45:32.901
```
