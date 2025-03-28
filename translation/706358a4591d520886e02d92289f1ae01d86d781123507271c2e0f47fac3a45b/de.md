```
sqrt(A::AbstractMatrix)
```

Wenn `A` keine negativen reellen Eigenwerte hat, berechne die Hauptmatrixwurzel von `A`, das heißt die eindeutige Matrix $X$ mit Eigenwerten, die einen positiven Realteil haben, sodass $X^2 = A$. Andernfalls wird eine nicht-hauptsächliche Wurzel zurückgegeben.

Wenn `A` reell-symmetrisch oder hermitesch ist, wird die Eigenzerlegung ([`eigen`](@ref)) verwendet, um die Wurzel zu berechnen. Für solche Matrizen werden Eigenwerte λ, die aufgrund von Rundungsfehlern leicht negativ erscheinen, so behandelt, als wären sie null. Genauer gesagt, werden Matrizen mit allen Eigenwerten `≥ -rtol*(max |λ|)` als semidefinit betrachtet (was eine hermitesche Wurzel ergibt), wobei negative Eigenwerte als null betrachtet werden. `rtol` ist ein Schlüsselwort-Argument für `sqrt` (nur im hermitesch/reell-symmetrischen Fall), das standardmäßig auf die Maschinenpräzision skaliert mit `size(A,1)` gesetzt ist.

Andernfalls wird die Wurzel mittels der Björck-Hammarling-Methode [^BH83] bestimmt, die die komplexe Schur-Form ([`schur`](@ref)) berechnet und dann die komplexe Wurzel des dreieckigen Faktors. Wenn eine reelle Wurzel existiert, wird stattdessen eine Erweiterung dieser Methode [^H87] verwendet, die die reelle Schur-Form berechnet und dann die reelle Wurzel des quasi-dreieckigen Faktors.

[^BH83]: Åke Björck und Sven Hammarling, "A Schur method for the square root of a matrix", Linear Algebra and its Applications, 52-53, 1983, 127-140. [doi:10.1016/0024-3795(83)80010-X](https://doi.org/10.1016/0024-3795(83)80010-X)

[^H87]: Nicholas J. Higham, "Computing real square roots of a real matrix", Linear Algebra and its Applications, 88-89, 1987, 405-430. [doi:10.1016/0024-3795(87)90118-2](https://doi.org/10.1016/0024-3795(87)90118-2)

# Beispiele

```jldoctest
julia> A = [4 0; 0 4]
2×2 Matrix{Int64}:
 4  0
 0  4

julia> sqrt(A)
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
