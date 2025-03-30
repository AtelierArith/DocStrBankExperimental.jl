```
svd(A, B) -> GenelSVD
```

`A` ve `B`'nin genel SVD'sini hesaplayın, `[A;B] = [F.U * F.D1; F.V * F.D2] * F.R0 * F.Q'` şeklinde bir `GeneralizedSVD` faktörizasyon nesnesi `F` döndürün.

  * `U` M-by-M ortogonal bir matristir,
  * `V` P-by-P ortogonal bir matristir,
  * `Q` N-by-N ortogonal bir matristir,
  * `D1` ilk K girişinde 1'ler bulunan M-by-(K+L) diyagonal bir matristir,
  * `D2` üst sağ L-by-L bloğu diyagonal olan P-by-(K+L) bir matristir,
  * `R0` sağdaki (K+L)-by-(K+L) bloğu tekil üst blok üçgen olan (K+L)-by-N bir matristir,

`K+L`, `[A; B]` matrisinin etkili sayısal derecesidir.

Ayrıştırmayı yinelemek `U`, `V`, `Q`, `D1`, `D2` ve `R0` bileşenlerini üretir.

Genel SVD, `A` ile `B` arasındaki karşılaştırmalar yapmak istendiğinde, insan ile maya genomu, sinyal ile gürültü veya kümeler arası ile kümeler içi gibi uygulamalarda kullanılır. (Tartışma için Edelman ve Wang'a bakın: https://arxiv.org/abs/1901.00485)

`[A; B]`'yi `[UC; VS]H` şeklinde ayrıştırır, burada `[UC; VS]`, `[A; B]`'nin sütun uzayı için doğal bir ortogonal temeldir ve `H = RQ'`, `[A;B]`'nin satır uzayı için doğal bir ortogonal olmayan temeldir; burada üst satırlar en çok `A` matrisine atfedilir ve alt satırlar `B` matrisine atfedilir. Çoklu kosinüs/sinüs matrisleri `C` ve `S`, `A` ile `B` arasındaki oranı ölçen çoklu bir ölçü sağlar ve `U` ile `V`, bunların ölçüldüğü yönleri sağlar.

# Örnekler

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
