```
addface!(name::Symbol => default::Face)
```

Erstelle ein neues Gesicht mit dem Namen `name`. Sofern kein Gesicht mit diesem Namen bereits existiert, wird `default` sowohl zu `FACES``.default` als auch (eine Kopie davon) zu `FACES`.`current` hinzugefügt, wobei der aktuelle Wert zurückgegeben wird.

Sollte das Gesicht `name` bereits existieren, wird `nothing` zurückgegeben.

# Beispiele

```jldoctest; setup = :(import StyledStrings: Face, addface!)
julia> addface!(:mypkg_myface => Face(slant=:italic, underline=true))
Face (sample)
         slant: italic
     underline: true
```
