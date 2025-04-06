```
hessenberg(A) -> Hessenberg
```

Berechnen Sie die Hessenberg-Zerlegung von `A` und geben Sie ein `Hessenberg`-Objekt zurück. Wenn `F` das Faktorisierungsobjekt ist, kann die unitäre Matrix mit `F.Q` (vom Typ `LinearAlgebra.HessenbergQ`) und die Hessenberg-Matrix mit `F.H` (vom Typ [`UpperHessenberg`](@ref)) zugegriffen werden, von denen jede in eine reguläre Matrix mit `Matrix(F.H)` oder `Matrix(F.Q)` umgewandelt werden kann.

Wenn `A` [`Hermitian`](@ref) oder reell-[`Symmetric`](@ref) ist, produziert die Hessenberg-Zerlegung eine reell-symmetrische tridiagonale Matrix und `F.H` ist vom Typ [`SymTridiagonal`](@ref).

Beachten Sie, dass die verschobene Faktorisierung `A+μI = Q (H+μI) Q'` effizient durch `F + μ*I` unter Verwendung des [`UniformScaling`](@ref) Objekts [`I`](@ref) konstruiert werden kann, das ein neues `Hessenberg`-Objekt mit gemeinsamem Speicher und einer modifizierten Verschiebung erstellt. Die Verschiebung eines gegebenen `F` wird durch `F.μ` erhalten. Dies ist nützlich, da mehrere verschobene Lösungen `(F + μ*I) \ b` (für unterschiedliche `μ` und/oder `b`) effizient durchgeführt werden können, sobald `F` erstellt ist.

Die Iteration der Zerlegung produziert die Faktoren `F.Q, F.H, F.μ`.

# Beispiele

```julia-repl
julia> A = [4. 9. 7.; 4. 4. 1.; 4. 3. 2.]
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> F = hessenberg(A)
Hessenberg{Float64, UpperHessenberg{Float64, Matrix{Float64}}, Matrix{Float64}, Vector{Float64}, Bool}
Q-Faktor: 3×3 LinearAlgebra.HessenbergQ{Float64, Matrix{Float64}, Vector{Float64}, false}
H-Faktor:
3×3 UpperHessenberg{Float64, Matrix{Float64}}:
  4.0      -11.3137       -1.41421
 -5.65685    5.0           2.0
   ⋅        -8.88178e-16   1.0

julia> F.Q * F.H * F.Q'
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> q, h = F; # Destrukturierung durch Iteration

julia> q == F.Q && h == F.H
true
```
