```
svd(A, B) -> GeneralizedSVD
```

Calcula la SVD generalizada de `A` y `B`, devolviendo un objeto de factorización `GeneralizedSVD` `F` tal que `[A;B] = [F.U * F.D1; F.V * F.D2] * F.R0 * F.Q'`

  * `U` es una matriz ortogonal de M por M,
  * `V` es una matriz ortogonal de P por P,
  * `Q` es una matriz ortogonal de N por N,
  * `D1` es una matriz diagonal de M por (K+L) con 1s en las primeras K entradas,
  * `D2` es una matriz de P por (K+L) cuyo bloque superior derecho de L por L es diagonal,
  * `R0` es una matriz de (K+L) por N cuyo bloque superior derecho de (K+L) por (K+L) es no singular y triangular superior,

`K+L` es el rango numérico efectivo de la matriz `[A; B]`.

Iterar la descomposición produce los componentes `U`, `V`, `Q`, `D1`, `D2` y `R0`.

La SVD generalizada se utiliza en aplicaciones como cuando se quiere comparar cuánto pertenece a `A` frente a cuánto pertenece a `B`, como en el genoma humano frente al de levadura, o señal frente a ruido, o entre clústeres frente a dentro de clústeres. (Ver Edelman y Wang para discusión: https://arxiv.org/abs/1901.00485)

Descompone `[A; B]` en `[UC; VS]H`, donde `[UC; VS]` es una base ortogonal natural para el espacio de columnas de `[A; B]`, y `H = RQ'` es una base no ortogonal natural para el espacio de filas de `[A;B]`, donde las filas superiores se atribuyen más estrechamente a la matriz `A`, y las inferiores a la matriz `B`. Las matrices multi-coseno/seno `C` y `S` proporcionan una medida múltiple de cuánto `A` frente a cuánto `B`, y `U` y `V` proporcionan direcciones en las que se miden.

# Ejemplos

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
