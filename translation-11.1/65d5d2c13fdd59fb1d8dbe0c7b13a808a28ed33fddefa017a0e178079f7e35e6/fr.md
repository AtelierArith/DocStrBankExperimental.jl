```
type primitif
```

`type primitif` déclare un type concret dont les données consistent uniquement en une série de bits. Des exemples classiques de types primitifs sont les entiers et les valeurs à virgule flottante. Voici quelques déclarations de types primitifs intégrés en exemple :

```julia
type primitif Char 32 fin
type primitif Bool <: Integer 8 fin
```

Le nombre après le nom indique combien de bits de stockage le type nécessite. Actuellement, seules les tailles qui sont des multiples de 8 bits sont prises en charge. La déclaration [`Bool`](@ref) montre comment un type primitif peut être déclaré en option comme un sous-type d'un supertype.
