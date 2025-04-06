```
rank(A::AbstractMatrix; atol::Gerçek=0, rtol::Gerçek=atol>0 ? 0 : n*ϵ)
rank(A::AbstractMatrix, rtol::Gerçek)
```

Bir matrisin sayısal sırasını, `svdvals(A)` çıktılarından kaç tanesinin `max(atol, rtol*σ₁)` değerinden büyük olduğunu sayarak hesaplayın; burada `σ₁`, `A`'nın hesaplanan en büyük tekil değeridir. `atol` ve `rtol` sırasıyla mutlak ve göreli toleranslardır. Varsayılan göreli tolerans `n*ϵ`'dir; burada `n`, `A`'nın en küçük boyutunun boyutudur ve `ϵ`, `A`'nın eleman türünün [`eps`](@ref) değeridir.

!!! not
    Sayısal sıra, eşik toleransı `max(atol, rtol*σ₁)`'ye yakın tekil değerlere sahip kötü koşullu matrislerin hassas ve belirsiz bir karakterizasyonu olabilir. Bu tür durumlarda, tekil değer hesaplamasına veya matrise yapılan küçük perturbasyonlar, `rank` sonucunu bir veya daha fazla tekil değeri eşik değerinin ötesine iterek değiştirebilir. Bu varyasyonlar, farklı Julia sürümleri, mimarileri, derleyicileri veya işletim sistemleri arasındaki kayan nokta hatalarındaki değişiklikler nedeniyle bile meydana gelebilir.


!!! uyum "Julia 1.1"
    `atol` ve `rtol` anahtar argümanları en az Julia 1.1 gerektirir. Julia 1.0'da `rtol` bir pozisyonel argüman olarak mevcuttur, ancak bu Julia 2.0'da kullanımdan kaldırılacaktır.


# Örnekler

```jldoctest
julia> rank(Matrix(I, 3, 3))
3

julia> rank(diagm(0 => [1, 0, 2]))
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.1)
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.00001)
3

julia> rank(diagm(0 => [1, 0.001, 2]), atol=1.5)
1
```
