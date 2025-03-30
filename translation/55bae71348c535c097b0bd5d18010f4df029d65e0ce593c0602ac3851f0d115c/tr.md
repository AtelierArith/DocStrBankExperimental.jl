```
hermitianpart!(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Kare matris `A`'yı yerinde Hermit kısmı `(A + A') / 2` ile üzerine yazın ve [`Hermitian(A, uplo)`](@ref) döndürün. Gerçek matrisler `A` için bu, `A`'nın simetrik kısmı olarak da bilinir.

Ayrıca [`hermitianpart`](@ref) ile ilgili yer dışı işlemi için bakın.

!!! uyumluluk "Julia 1.10"
    Bu fonksiyon Julia 1.10 veya daha yenisini gerektirir.

