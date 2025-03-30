```
MIME
```

Standart bir internet veri formatını temsil eden bir tür. "MIME", "Çok Amaçlı İnternet Posta Uzantıları"nın kısaltmasıdır, çünkü standart başlangıçta e-posta mesajlarına çoklu ortam eklerini tanımlamak için kullanılmıştır.

Bir `MIME` nesnesi, o formatta çıktı talep etmek için [`show`](@ref) fonksiyonuna ikinci argüman olarak geçirilebilir.

# Örnekler

```jldoctest
julia> show(stdout, MIME("text/plain"), "hi")
"hi"
```
