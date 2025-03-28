```
svd(A, B) -> GeneralizedSVD
```

Berechnen Sie die verallgemeinerte SVD von `A` und `B`, die ein `GeneralizedSVD`-Faktorisierungsobjekt `F` zurückgibt, sodass `[A;B] = [F.U * F.D1; F.V * F.D2] * F.R0 * F.Q'`

  * `U` ist eine M-by-M orthogonale Matrix,
  * `V` ist eine P-by-P orthogonale Matrix,
  * `Q` ist eine N-by-N orthogonale Matrix,
  * `D1` ist eine M-by-(K+L) diagonale Matrix mit 1en in den ersten K Einträgen,
  * `D2` ist eine P-by-(K+L) Matrix, deren oberer rechter L-by-L Block diagonal ist,
  * `R0` ist eine (K+L)-by-N Matrix, deren rechtester (K+L)-by-(K+L) Block nicht-singulär oberblocktriangular ist,

`K+L` ist der effektive numerische Rang der Matrix `[A; B]`.

Das Iterieren der Zerlegung produziert die Komponenten `U`, `V`, `Q`, `D1`, `D2` und `R0`.

Die verallgemeinerte SVD wird in Anwendungen verwendet, wie z.B. wenn man vergleichen möchte, wie viel zu `A` vs. wie viel zu `B` gehört, wie im menschlichen vs. Hefegenom, oder Signal vs. Rauschen, oder zwischen Clustern vs. innerhalb von Clustern. (Siehe Edelman und Wang für eine Diskussion: https://arxiv.org/abs/1901.00485)

Sie zerlegt `[A; B]` in `[UC; VS]H`, wobei `[UC; VS]` eine natürliche orthogonale Basis für den Spaltenraum von `[A; B]` ist, und `H = RQ'` eine natürliche nicht-orthogonale Basis für den Zeilenraum von `[A;B]`, wobei die obersten Zeilen am engsten dem `A`-Matrix zugeordnet sind und die unteren der `B`-Matrix. Die Multi-Cosinus/Sinus-Matrizen `C` und `S` bieten eine Multi-Messung dafür, wie viel `A` vs wie viel `B`, und `U` und `V` bieten Richtungen, in denen diese gemessen werden.

# Beispiele

```jldoctest
julia> A = randn(3,2); B=randn(4,2);

julia> F = svd(A, B);

julia> U,V,Q,C,S,R = F;

julia> H = R*Q';

julia> [A; B] ≈ [U*C; V*S]*H
true

julia> [A; B] ≈ [F.U*F.D1; F.V*F.D2]*F.R0*F.Q'
true

julia> Uonly, = svd(A,B);

julia> U == Uonly
true
```
