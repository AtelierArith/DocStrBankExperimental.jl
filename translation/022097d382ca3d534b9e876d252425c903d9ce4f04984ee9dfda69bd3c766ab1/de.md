```
reim(A::AbstractArray)
```

Gibt ein Tupel von zwei Arrays zurück, die jeweils den Real- und den Imaginärteil jedes Eintrags in `A` enthalten.

Entspricht `(real.(A), imag.(A))`, es sei denn, `eltype(A) <: Real`, in diesem Fall wird `A` ohne Kopieren zurückgegeben, um den Realteil darzustellen, und wenn `A` null Dimensionen hat, wird ein 0-dimensionales Array zurückgegeben (anstatt eines Skalars).

# Beispiele

```jldoctest
julia> reim([1, 2im, 3 + 4im])
([1, 0, 3], [0, 2, 4])

julia> reim(fill(2 - im))
(fill(2), fill(-1))
```
