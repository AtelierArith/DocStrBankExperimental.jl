```
Event([autoreset=false])
```

Seviye tetikleyici bir olay kaynağı oluşturur. [`wait`](@ref) çağrısı yapan görevler, `Event` üzerinde `notify` çağrısı yapılana kadar askıya alınır ve sıraya alınır. `notify` çağrısı yapıldıktan sonra, `Event` bir sinyal durumunda kalır ve görevler artık beklerken engellenmez, ta ki `reset` çağrısı yapılana kadar.

Eğer `autoreset` doğruysa, her `notify` çağrısı için en fazla bir görev `wait`'ten serbest bırakılacaktır.

Bu, notify/wait üzerinde bir edinme ve serbest bırakma bellek sıralaması sağlar.

!!! compat "Julia 1.1"
    Bu işlevsellik en az Julia 1.1 gerektirir.


!!! compat "Julia 1.8"
    `autoreset` işlevselliği ve bellek sıralama garantisi en az Julia 1.8 gerektirir.

