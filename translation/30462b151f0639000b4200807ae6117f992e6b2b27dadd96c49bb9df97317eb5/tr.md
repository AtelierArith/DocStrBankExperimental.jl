lock(f::Function, l::Lockable)

`l` ile ilişkili kilidi al, `f`'yi kilitli olarak çalıştır ve `f` döndüğünde kilidi serbest bırak. `f`, `l` tarafından sarılmış olan değeri alan bir konumsal argüman alacaktır. Eğer kilit başka bir görev/işlem tarafından zaten kilitlenmişse, kullanılabilir hale gelene kadar bekle. Bu fonksiyon döndüğünde, `lock` serbest bırakılmıştır, bu nedenle çağıran kişi onu `unlock` etmeye çalışmamalıdır.

!!! compat "Julia 1.11"
    En az Julia 1.11 gerektirir.

