```
IndexStyle(A)
IndexStyle(typeof(A))
```

`IndexStyle`, dizi `A` için "yerel indeksleme stilini" belirtir. Yeni bir [`AbstractArray`](@ref) türü tanımladığınızda, ya lineer indeksleme ([`IndexLinear`](@ref) ile) ya da kartezyen indeksleme uygulamayı seçebilirsiniz. Sadece lineer indeksleme uygulamaya karar verirseniz, o zaman bu özelliği dizi türünüz için ayarlamalısınız:

```
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

Varsayılan [`IndexCartesian()`](@ref) 'dir.

Julia'nın dahili indeksleme mekanizması, tüm indeksleme işlemlerini otomatik olarak (ve görünmez bir şekilde) tercih edilen stile yeniden hesaplayacaktır. Bu, kullanıcıların, açık yöntemler sağlanmamış olsa bile, dizinizin elemanlarına herhangi bir indeksleme stili kullanarak erişmelerine olanak tanır.

`AbstractArray`'ınız için her iki indeksleme stilini tanımlarsanız, bu özellik en performanslı indeksleme stilini seçmek için kullanılabilir. Bazı yöntemler, girdilerinde bu özelliği kontrol eder ve en verimli erişim desenine bağlı olarak farklı algoritmalara yönlendirme yapar. Özellikle, [`eachindex`](@ref) bu özelliğin ayarına bağlı olarak türü değişen bir yineleyici oluşturur.
