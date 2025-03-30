```
atexit(f)
```

Bir sıfır veya bir argümanlı `f()` fonksiyonunu işlem çıkışında çağrılmak üzere kaydedin. `atexit()` kancaları son giren ilk çıkar (LIFO) sırasına göre çağrılır ve nesne sonlandırıcılarından önce çalıştırılır.

Eğer `f` için bir tam sayı argümanı tanımlanmış bir yöntem varsa, `f(n::Int32)` olarak çağrılacaktır; burada `n` mevcut çıkış kodudur, aksi takdirde `f()` olarak çağrılacaktır.

!!! compat "Julia 1.9"
    Tek argümanlı form Julia 1.9 gerektirir.


Çıkış kancalarının `exit(n)` çağrısında bulunmasına izin verilir; bu durumda Julia çıkış kodu `n` ile çıkacaktır (orijinal çıkış kodu yerine). Eğer birden fazla çıkış kancası `exit(n)` çağrısında bulunursa, Julia, `exit(n)` çağrısında bulunan son çağrılan çıkış kancasına karşılık gelen çıkış kodu ile çıkacaktır. (Çünkü çıkış kancaları LIFO sırasına göre çağrılır, "son çağrılan" ifadesi "ilk kaydedilen" ile eşdeğerdir.)

Not: Tüm çıkış kancaları çağrıldıktan sonra, daha fazla çıkış kancası kaydedilemez ve tüm kancalar tamamlandıktan sonra `atexit(f)` çağrısı yapmak bir istisna fırlatır. Bu durum, arka planda hala eşzamanlı olarak çalışan Görevlerden çıkış kancaları kaydediyorsanız meydana gelebilir.
