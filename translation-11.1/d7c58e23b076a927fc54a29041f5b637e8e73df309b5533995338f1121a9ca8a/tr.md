```
sparse!(I::AbstractVector{Ti}, J::AbstractVector{Ti}, V::AbstractVector{Tv},
        m::Integer, n::Integer, combine, klasttouch::Vector{Ti},
        csrrowptr::Vector{Ti}, csrcolval::Vector{Ti}, csrnzval::Vector{Tv},
        [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}] ) where {Tv,Ti<:Integer}
```

[`sparse`](@ref) için ebeveyn ve uzman sürücü; temel kullanım için [`sparse`](@ref) sayfasına bakın. Bu yöntem, kullanıcının aşağıda açıklanan `sparse`'ın ara nesneleri ve sonuçları için önceden tahsis edilmiş depolama sağlamasına olanak tanır. Bu yetenek, koordinat temsillerinden [`SparseMatrixCSC`](@ref) oluşturulmasını daha verimli hale getirir ve ayrıca sonucun transpozunun sıralanmamış sütun temsilinin ek bir maliyet olmaksızın çıkarılmasını sağlar.

Bu yöntem üç ana adımdan oluşur: (1) Sağlanan koordinat temsilini, tekrar eden girişleri de içeren sıralanmamış satır CSR biçimine sayım sıralaması ile yerleştirmek. (2) CSR biçiminde süzülerek, istenen CSC biçiminin sütun işaretçi dizisini hesaplamak, tekrar eden girişleri tespit etmek ve CSR biçimini tekrar eden girişlerle yeniden paketlemek; bu aşama, tekrar eden girişler içermeyen sıralanmamış satır CSR biçimini verir. (3) Önceki CSR biçimini, tekrar eden girişler içermeyen tamamen sıralı bir CSC biçimine sayım sıralaması ile yerleştirmek.

Girdi dizileri `csrrowptr`, `csrcolval` ve `csrnzval`, ara CSR biçimleri için depolama oluşturur ve `length(csrrowptr) >= m + 1`, `length(csrcolval) >= length(I)` ve `length(csrnzval >= length(I))` gerektirir. İkinci aşama için çalışma alanı olan girdi dizisi `klasttouch`, `length(klasttouch) >= n` gerektirir. Opsiyonel girdi dizileri `csccolptr`, `cscrowval` ve `cscnzval`, döndürülen CSC biçimi `S` için depolama oluşturur. Gerekirse, bunlar otomatik olarak `length(csccolptr) = n + 1`, `length(cscrowval) = nnz(S)` ve `length(cscnzval) = nnz(S)` koşullarını karşılayacak şekilde yeniden boyutlandırılır; bu nedenle, `nnz(S)` başlangıçta bilinmiyorsa, uygun türde boş vektörler (`Vector{Ti}()` ve `Vector{Tv}()`) geçmek yeterlidir veya `cscrowval` ve `cscnzval`'ı göz ardı ederek `sparse!` yöntemini çağırmak yeterlidir.

Dönüşte, `csrrowptr`, `csrcolval` ve `csrnzval`, sonucun transpozunun sıralanmamış sütun temsilini içerir.

Girdi dizilerinin depolamasını (`I`, `J`, `V`) çıktı dizileri (`csccolptr`, `cscrowval`, `cscnzval`) için yeniden kullanabilirsiniz. Örneğin, `sparse!(I, J, V, csrrowptr, csrcolval, csrnzval, I, J, V)` çağrısını yapabilirsiniz. Bunların yukarıdaki koşulları karşılayacak şekilde yeniden boyutlandırılacağını unutmayın.

Verimlilik açısından, bu yöntem `1 <= I[k] <= m` ve `1 <= J[k] <= n` dışında hiçbir argüman kontrolü yapmaz. Dikkatli kullanın. `--check-bounds=yes` ile test etmek akıllıca olacaktır.

Bu yöntem `O(m, n, length(I))` zamanında çalışır. F. Gustavson'un "Sparse Matrisler için iki hızlı algoritma: çarpma ve permütasyon transpozisyonu," ACM TOMS 4(3), 250-269 (1978) adlı eserinde tanımlanan HALFPERM algoritması, bu yöntemin bir çift sayım sıralaması kullanmasını ilham etmiştir.
