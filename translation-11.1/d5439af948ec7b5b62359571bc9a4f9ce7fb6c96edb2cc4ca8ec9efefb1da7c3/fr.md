```
CartesianIndices(sz::Dims) -> R
CartesianIndices((istart:[istep:]istop, jstart:[jstep:]jstop, ...)) -> R
```

Définissez une région `R` s'étendant sur une plage rectangulaire multidimensionnelle d'indices entiers. Ceux-ci sont le plus souvent rencontrés dans le contexte de l'itération, où `for I in R ... end` renverra des indices [`CartesianIndex`](@ref) `I` équivalents aux boucles imbriquées

```
for j = jstart:jstep:jstop
    for i = istart:istep:istop
        ...
    end
end
```

Par conséquent, ceux-ci peuvent être utiles pour écrire des algorithmes qui fonctionnent dans des dimensions arbitraires.

```
CartesianIndices(A::AbstractArray) -> R
```

Par commodité, la construction d'un `CartesianIndices` à partir d'un tableau crée une plage de ses indices.

!!! compat "Julia 1.6"
    La méthode de plage d'étape `CartesianIndices((istart:istep:istop, jstart:[jstep:]jstop, ...))` nécessite au moins Julia 1.6.


# Exemples

```jldoctest
julia> foreach(println, CartesianIndices((2, 2, 2)))
CartesianIndex(1, 1, 1)
CartesianIndex(2, 1, 1)
CartesianIndex(1, 2, 1)
CartesianIndex(2, 2, 1)
CartesianIndex(1, 1, 2)
CartesianIndex(2, 1, 2)
CartesianIndex(1, 2, 2)
CartesianIndex(2, 2, 2)

julia> CartesianIndices(fill(1, (2,3)))
CartesianIndices((2, 3))
```

## Conversion entre indices linéaires et cartésiens

La conversion d'un indice linéaire à un indice cartésien exploite le fait qu'un `CartesianIndices` est un `AbstractArray` et peut être indexé linéairement :

```jldoctest
julia> cartesian = CartesianIndices((1:3, 1:2))
CartesianIndices((1:3, 1:2))

julia> cartesian[4]
CartesianIndex(1, 2)

julia> cartesian = CartesianIndices((1:2:5, 1:2))
CartesianIndices((1:2:5, 1:2))

julia> cartesian[2, 2]
CartesianIndex(3, 2)
```

## Diffusion

`CartesianIndices` prend en charge l'arithmétique de diffusion (+ et -) avec un `CartesianIndex`.

!!! compat "Julia 1.1"
    La diffusion de CartesianIndices nécessite au moins Julia 1.1.


```jldoctest
julia> CIs = CartesianIndices((2:3, 5:6))
CartesianIndices((2:3, 5:6))

julia> CI = CartesianIndex(3, 4)
CartesianIndex(3, 4)

julia> CIs .+ CI
CartesianIndices((5:6, 9:10))
```

Pour la conversion d'un indice cartésien à un indice linéaire, voir [`LinearIndices`](@ref).
