```
\(A, B)
```

Bir polialgoritma kullanarak matris bölme. Girdi matrisleri `A` ve `B` için sonuç `X`, `A` kare olduğunda `A*X == B` olacak şekilde tanımlanır. Kullanılan çözücü, `A`'nın yapısına bağlıdır. Eğer `A` üst veya alt üçgen (veya diyagonal) ise, `A`'nın faktörizasyonuna gerek yoktur ve sistem ileri veya geri yerine koyma ile çözülür. Üçgen olmayan kare matrisler için LU faktörizasyonu kullanılır.

Dikdörtgen `A` için sonuç, `A`'nın pivotlu QR faktörizasyonu ve `A`'nın R faktörüne dayanan bir sıralama tahmini ile hesaplanan minimum-norm en küçük kareler çözümüdür.

`A` seyrek olduğunda, benzer bir polialgoritma kullanılır. Belirsiz matrisler için, `LDLt` faktörizasyonu sayısal faktörizasyon sırasında pivotlama kullanmaz ve bu nedenle prosedür, tersine çevrilebilir matrisler için bile başarısız olabilir.

Ayrıca bakınız: [`factorize`](@ref), [`pinv`](@ref).

# Örnekler

```jldoctest
julia> A = [1 0; 1 -2]; B = [32; -4];

julia> X = A \ B
2-element Vector{Float64}:
 32.0
 18.0

julia> A * X == B
true
```
