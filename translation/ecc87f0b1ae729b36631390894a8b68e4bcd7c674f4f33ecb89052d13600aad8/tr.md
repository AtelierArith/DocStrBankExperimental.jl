```
SparseArrays.sparse!(I, J, V, [m, n, combine]) -> SparseMatrixCSC
```

Giriş vektörlerini (`I`, `J`, `V`) son matris depolaması için yeniden kullanan `sparse!`'ın bir varyantı. Yapıdan sonra giriş vektörleri matris tamponlarıyla alias olacak; `S.colptr === I`, `S.rowval === J` ve `S.nzval === V` geçerlidir ve gerektiğinde `resize!` yapılacaktır.

Bazı çalışma tamponlarının hala tahsis edileceğini unutmayın. Özellikle, bu yöntem `sparse!(I, J, V, m, n, combine, klasttouch, csrrowptr, csrcolval, csrnzval, csccolptr, cscrowval, cscnzval)` etrafında bir kolaylık sarmalayıcıdır; bu yöntem uygun boyutta `klasttouch`, `csrrowptr`, `csrcolval` ve `csrnzval` tahsis eder, ancak `csccolptr`, `cscrowval` ve `cscnzval` için `I`, `J` ve `V`'yi yeniden kullanır.

`m`, `n` ve `combine` argümanları sırasıyla `maximum(I)`, `maximum(J)` ve `+` olarak varsayılan değerlerdir.

!!! uyumluluk "Julia 1.10"
    Bu yöntem Julia sürümü 1.10 veya daha yenisini gerektirir.

