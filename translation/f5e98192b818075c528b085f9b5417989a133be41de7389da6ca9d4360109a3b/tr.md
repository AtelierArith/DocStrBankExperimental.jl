```
hermitianpart(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Kare matris `A`'nın Hermit kısmını döndürür; bu, `(A + A') / 2` olarak tanımlanır ve bir [`Hermitian`](@ref) matrisidir. Gerçek matrisler `A` için bu, `A`'nın simetrik kısmı olarak da bilinir; bazen "operatör gerçek kısmı" olarak da adlandırılır. İsteğe bağlı `uplo` argümanı, [`Hermitian`](@ref) görünümünün karşılık gelen argümanını kontrol eder. Gerçek matrisler için, bu sonuncusu bir [`Symmetric`](@ref) görünümüne eşdeğerdir.

Ayrıca, karşılık gelen yerinde işlem için [`hermitianpart!`](@ref) fonksiyonuna da bakın.

!!! compat "Julia 1.10"
    Bu fonksiyon Julia 1.10 veya daha yenisini gerektirir.

