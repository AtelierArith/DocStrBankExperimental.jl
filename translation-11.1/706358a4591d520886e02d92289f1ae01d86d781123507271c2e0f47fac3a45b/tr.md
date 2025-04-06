```
sqrt(A::AbstractMatrix)
```

Eğer `A` negatif gerçek özdeğerlere sahip değilse, `A`'nın ana matris karekökünü hesaplayın, yani $X^2 = A$ olacak şekilde pozitif gerçek parçaya sahip özdeğerlere sahip olan benzersiz matris. Aksi takdirde, bir nonprincipal karekök döndürülür.

Eğer `A` gerçek-simetrik veya Hermit ise, karekökü hesaplamak için özdeğerlendirmesi ([`eigen`](@ref)) kullanılır. Bu tür matrisler için, yuvarlama hataları nedeniyle hafif negatif görünen özdeğerler sıfırmış gibi kabul edilir. Daha kesin olarak, tüm özdeğerleri `≥ -rtol*(max |λ|)` olan matrisler yarı belirli olarak kabul edilir (Hermit karekökü verir), negatif özdeğerler sıfır olarak alınır. `rtol`, `sqrt`'a (sadece Hermit/gerçek-simetrik durumda) varsayılan olarak `size(A,1)` ile ölçeklendirilmiş makine hassasiyeti olan bir anahtar argümandır.

Aksi takdirde, karekök, karmaşık Schur formunu ([`schur`](@ref)) hesaplayan ve ardından üçgen faktörün karmaşık karekökünü hesaplayan Björck-Hammarling yöntemi ile belirlenir. Eğer gerçek bir karekök varsa, bu yöntemin [^H87] gerçek Schur formunu hesaplayan ve ardından quasi-üçgen faktörün gerçek karekökünü hesaplayan bir uzantısı kullanılır.

[^BH83]: Åke Björck ve Sven Hammarling, "A Schur method for the square root of a matrix", Linear Algebra and its Applications, 52-53, 1983, 127-140. [doi:10.1016/0024-3795(83)80010-X](https://doi.org/10.1016/0024-3795(83)80010-X)

[^H87]: Nicholas J. Higham, "Computing real square roots of a real matrix", Linear Algebra and its Applications, 88-89, 1987, 405-430. [doi:10.1016/0024-3795(87)90118-2](https://doi.org/10.1016/0024-3795(87)90118-2)

# Örnekler

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
