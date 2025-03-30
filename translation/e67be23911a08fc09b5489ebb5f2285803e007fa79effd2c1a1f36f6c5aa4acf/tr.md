```
run(command, args...; wait::Bool = true)
```

Bir komut nesnesini çalıştırır, geri tırnaklarla oluşturulmuştur (bkz. kılavuzdaki [Dış Programları Çalıştırma](@ref) bölümü). Bir şeyler ters giderse, hata fırlatır; bu, sürecin sıfırdan farklı bir durum kodu ile çıkması da dahil (eğer `wait` true ise).

`args...` komuta dosya tanımlayıcıları geçirmenize olanak tanır ve normal unix dosya tanımlayıcıları gibi sıralanır (örneğin `stdin, stdout, stderr, FD(3), FD(4)...`).

Eğer `wait` false ise, süreç asenkron olarak çalışır. Daha sonra onun için bekleyebilir ve döndürülen süreç nesnesinde `success` çağrısı yaparak çıkış durumunu kontrol edebilirsiniz.

Eğer `wait` false ise, sürecin G/Ç akışları `devnull`'a yönlendirilir. Eğer `wait` true ise, G/Ç akışları ana süreçle paylaşılır. G/Ç yönlendirmesini kontrol etmek için [`pipeline`](@ref) kullanın.
