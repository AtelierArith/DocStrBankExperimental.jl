```
@printf([io::IO], "%Fmt", args...)
```

Imprime `args` en utilisant une chaîne de spécification de format de style C `printf`. En option, un `IO` peut être passé comme premier argument pour rediriger la sortie.

# Exemples

```jldoctest
julia> @printf "Hello %s" "world"
Hello world

julia> @printf "Scientific notation %e" 1.234
Notation scientifique 1.234000e+00

julia> @printf "Scientific notation three digits %.3e" 1.23456
Notation scientifique trois chiffres 1.235e+00

julia> @printf "Decimal two digits %.2f" 1.23456
Décimal deux chiffres 1.23

julia> @printf "Padded to length 5 %5i" 123
Rempli à la longueur 5   123

julia> @printf "Padded with zeros to length 6 %06i" 123
Rempli avec des zéros à la longueur 6 000123

julia> @printf "Use shorter of decimal or scientific %g %g" 1.23 12300000.0
Utiliser le plus court entre décimal ou scientifique 1.23 1.23e+07

julia> @printf "Use dynamic width and precision  %*.*f" 10 2 0.12345
Utiliser une largeur et une précision dynamiques        0.12
```

Pour une spécification systématique du format, voir [ici](https://en.cppreference.com/w/c/io/fprintf). Voir aussi [`@sprintf`](@ref) pour obtenir le résultat sous forme de `String` au lieu d'être imprimé.

# Avertissements

`Inf` et `NaN` sont imprimés de manière cohérente comme `Inf` et `NaN` pour les indicateurs `%a`, `%A`, `%e`, `%E`, `%f`, `%F`, `%g`, et `%G`. De plus, si un nombre à virgule flottante est également proche des valeurs numériques de deux chaînes de sortie possibles, la chaîne de sortie la plus éloignée de zéro est choisie.

# Exemples

```jldoctest
julia> @printf("%f %F %f %F", Inf, Inf, NaN, NaN)
Inf Inf NaN NaN

julia> @printf "%.0f %.1f %f" 0.5 0.025 -0.0078125
0 0.0 -0.007812
```

!!! compat "Julia 1.8"
    À partir de Julia 1.8, les largeurs de `%s` (chaîne) et `%c` (caractère) sont calculées en utilisant [`textwidth`](@ref), qui par exemple ignore les caractères de largeur nulle (comme les caractères combinants pour les signes diacritiques) et traite certains caractères "larges" (par exemple les émojis) comme ayant une largeur de `2`.


!!! compat "Julia 1.10"
    Les spécificateurs de largeur dynamique comme `%*s` et `%0*.*f` nécessitent Julia 1.10.


```
