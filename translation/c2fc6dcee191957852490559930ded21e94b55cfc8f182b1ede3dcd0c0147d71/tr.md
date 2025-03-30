```
LazyString <: AbstractString
```

Bir dizi interpolasyonunun tembel bir temsili. Bu, bir dizinin, gerçek interpolasyonun ve dizi inşasının gereksiz veya istenmeyen olduğu bir bağlamda oluşturulması gerektiğinde faydalıdır (örneğin, işlevlerin hata yollarında).

Bu tür, çalışma zamanında inşa edilmesi için ucuz olacak şekilde tasarlanmıştır ve mümkün olduğunca fazla işi makroya veya daha sonraki yazdırma işlemlerine devretmeye çalışır.

# Örnekler

```jldoctest
julia> n = 5; str = LazyString("n is ", n)
"n is 5"
```

Ayrıca [`@lazy_str`](@ref) bakınız.

!!! compat "Julia 1.8"
    `LazyString`, Julia 1.8 veya daha yenisini gerektirir.


# Genişletilmiş yardım

## Eşzamanlı programlar için güvenlik özellikleri

Bir tembel dizi, birden fazla Julia görevinde yazdırılsa bile, kendisi herhangi bir eşzamanlılık problemi oluşturmaz. Ancak, yakalanmış bir değerin `print` yöntemleri, senkronizasyon olmadan çağrıldığında bir eşzamanlılık sorunu yaşayabilir; tembel dizinin yazdırılması bir sorun yaratabilir. Ayrıca, yakalanmış değerler üzerindeki `print` yöntemleri birden fazla kez çağrılabilir, ancak yalnızca tam olarak bir sonuç dönecektir.

!!! compat "Julia 1.9"
    `LazyString`, yukarıdaki anlamda Julia 1.9 ve sonrasında güvenlidir.

