```
SparseArrays.spzeros!(::Type{Tv}, I, J, [m, n]) -> SparseMatrixCSC{Tv}
```

Giriş vektörleri `I` ve `J`'yi son matris depolaması için yeniden kullanan `spzeros!`'ın bir varyantı. İnşa edildikten sonra giriş vektörleri matris tamponlarıyla alias olacak; `S.colptr === I` ve `S.rowval === J` geçerlidir ve gerektiğinde `resize!` yapılacaktır.

Bazı çalışma tamponlarının hala tahsis edileceğini unutmayın. Özellikle, bu yöntem `spzeros!(Tv, I, J, m, n, klasttouch, csrrowptr, csrcolval, csccolptr, cscrowval)` etrafında bir kolaylık sarmalayıcıdır; bu yöntem uygun boyutta `klasttouch`, `csrrowptr` ve `csrcolval` tahsis eder, ancak `csccolptr` ve `cscrowval` için `I` ve `J`'yi yeniden kullanır.

`m` ve `n` argümanları varsayılan olarak `maximum(I)` ve `maximum(J)`'dir.

!!! compat "Julia 1.10"
    Bu yöntem Julia sürümü 1.10 veya daha yenisini gerektirir.

