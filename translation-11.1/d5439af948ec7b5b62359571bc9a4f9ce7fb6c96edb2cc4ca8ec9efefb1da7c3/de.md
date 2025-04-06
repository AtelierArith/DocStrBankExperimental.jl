```
CartesianIndices(sz::Dims) -> R
CartesianIndices((istart:[istep:]istop, jstart:[jstep:]jstop, ...)) -> R
```

Definieren Sie einen Bereich `R`, der einen mehrdimensionalen rechteckigen Bereich von ganzzahligen Indizes umfasst. Diese werden am häufigsten im Kontext der Iteration verwendet, wo `for I in R ... end` [`CartesianIndex`](@ref) Indizes `I` zurückgibt, die den geschachtelten Schleifen entsprechen

```
for j = jstart:jstep:jstop
    for i = istart:istep:istop
        ...
    end
end
```

Folglich können diese nützlich sein, um Algorithmen zu schreiben, die in beliebigen Dimensionen arbeiten.

```
CartesianIndices(A::AbstractArray) -> R
```

Zur Vereinfachung erstellt die Konstruktion eines `CartesianIndices` aus einem Array einen Bereich seiner Indizes.

!!! compat "Julia 1.6"
    Die Schrittbereichsmethode `CartesianIndices((istart:istep:istop, jstart:[jstep:]jstop, ...))` erfordert mindestens Julia 1.6.


# Beispiele

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

## Umwandlung zwischen linearen und kartesischen Indizes

Die Umwandlung von linearen Indizes in kartesische Indizes nutzt die Tatsache aus, dass ein `CartesianIndices` ein `AbstractArray` ist und linear indiziert werden kann:

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

## Broadcasting

`CartesianIndices` unterstützen die Broadcasting-Arithmetik (+ und -) mit einem `CartesianIndex`.

!!! compat "Julia 1.1"
    Broadcasting von CartesianIndices erfordert mindestens Julia 1.1.


```jldoctest
julia> CIs = CartesianIndices((2:3, 5:6))
CartesianIndices((2:3, 5:6))

julia> CI = CartesianIndex(3, 4)
CartesianIndex(3, 4)

julia> CIs .+ CI
CartesianIndices((5:6, 9:10))
```

Für die Umwandlung von kartesischen zu linearen Indizes siehe [`LinearIndices`](@ref). ```
