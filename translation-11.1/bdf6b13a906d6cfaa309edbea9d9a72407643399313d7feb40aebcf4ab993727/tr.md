```
sonunda
```

Verilen bir kod bloğu çıkarken, çıkış şekli ne olursa olsun bazı kodlar çalıştırın. Örneğin, açılmış bir dosyanın kapatılmasını garanti etmenin yolu şu şekildedir:

```julia
f = open("file")
try
    operate_on_file(f)
finally
    close(f)
end
```

Kontrol [`try`](@ref) bloğundan çıktığında (örneğin, bir [`return`](@ref) nedeniyle veya normal bir şekilde bitirdiğinde), [`close(f)`](@ref) çalıştırılacaktır. Eğer `try` bloğu bir istisna nedeniyle çıkarsa, istisna yayılmaya devam edecektir. Bir `catch` bloğu `try` ve `finally` ile birleştirilebilir. Bu durumda `finally` bloğu, `catch` hatayı işledikten sonra çalışacaktır.
