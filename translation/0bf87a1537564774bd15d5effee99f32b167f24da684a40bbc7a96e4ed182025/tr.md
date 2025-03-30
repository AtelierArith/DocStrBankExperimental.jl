```
localindices(S::SharedArray)
```

Mevcut işlem tarafından işlenmesi gereken "varsayılan" indeksleri tanımlayan bir aralık döndürür. Bu aralık, lineer indeksleme anlamında yorumlanmalıdır, yani `1:length(S)`'nin bir alt aralığı olarak. Çoklu işlem bağlamlarında, ana işlemde (veya [`indexpids`](@ref) 0 döndüren herhangi bir işlemde) boş bir aralık döner.

`localindices`'in tamamen bir kolaylık olarak var olduğunu vurgulamak önemlidir ve dizideki işleri işçiler arasında istediğiniz şekilde bölümlendirebilirsiniz. Bir `SharedArray` için, tüm indeksler her işçi işlemi için eşit derecede hızlı olmalıdır.
