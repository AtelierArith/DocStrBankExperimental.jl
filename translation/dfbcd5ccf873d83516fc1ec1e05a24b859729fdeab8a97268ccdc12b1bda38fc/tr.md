```
arg_readers(arg :: AbstractString, [ type = ArgRead ]) do arg::Function
    ## ön test kurulumu ##
    @arg_test arg begin
        arg :: ArgRead
        ## `arg` kullanarak test ##
    end
    ## test sonrası temizlik ##
end
```

`arg_readers` fonksiyonu okunacak bir yol ve bir tek-argümanlı do bloğu alır; bu blok, `arg_read`'in işleyebileceği her test okuyucu türü için bir kez çağrılır. İsteğe bağlı `type` argümanı verilirse, do bloğu yalnızca o türde argüman üreten okuyucular için çağrılır.

Do bloğuna geçirilen `arg`, argüman değerinin kendisi değildir, çünkü bazı test argüman türlerinin her test durumu için başlatılması ve sonlandırılması gerekir. Açık bir dosya tanıtıcısı argümanını düşünün: bir testi kullandıktan sonra, onu tekrar kullanamazsınız; bir sonraki test için dosyayı kapatıp tekrar açmanız gerekir. Bu `arg` fonksiyonu, `@arg_test arg begin ... end` kullanılarak bir `ArgRead` örneğine dönüştürülebilir.
