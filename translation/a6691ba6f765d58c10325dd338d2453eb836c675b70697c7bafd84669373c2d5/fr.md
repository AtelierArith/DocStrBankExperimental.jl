```
addface!(name::Symbol => default::Face)
```

Créez un nouveau visage par le nom `name`. Tant qu'aucun visage n'existe déjà sous ce nom, `default` est ajouté à la fois à `FACES``.default` et (une copie de) à `FACES`.`current`, avec la valeur actuelle retournée.

Si le visage `name` existe déjà, `nothing` est retourné.

# Exemples

```jldoctest; setup = :(import StyledStrings: Face, addface!)
julia> addface!(:mypkg_myface => Face(slant=:italic, underline=true))
Face (échantillon)
         slant: italic
     underline: true
```
