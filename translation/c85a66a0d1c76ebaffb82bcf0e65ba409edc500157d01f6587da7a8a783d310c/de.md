```
showable(mime, x)
```

Gibt einen booleschen Wert zurück, der angibt, ob das Objekt `x` als der angegebene `mime`-Typ geschrieben werden kann.

(Im Allgemeinen wird dies automatisch durch die Existenz der entsprechenden [`show`](@ref)-Methode für `typeof(x)` bestimmt. Einige Typen bieten benutzerdefinierte `showable`-Methoden an; zum Beispiel, wenn die verfügbaren MIME-Formate von dem *Wert* von `x` abhängen.)

# Beispiele

```jldoctest
julia> showable(MIME("text/plain"), rand(5))
true

julia> showable("image/png", rand(5))
false
```
