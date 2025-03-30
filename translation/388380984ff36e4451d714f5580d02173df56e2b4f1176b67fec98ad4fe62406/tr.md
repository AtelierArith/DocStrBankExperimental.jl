```
arg_writers([ type = ArgWrite ]) do path::String, arg::Function
    ## ön test kurulumu ##
    @arg_test arg begin
        arg :: ArgWrite
        ## `arg` kullanarak test ##
    end
    ## test sonrası temizlik ##
end
```

`arg_writers` fonksiyonu, `arg_write`'ın işleyebileceği her test yazıcı türü için bir kez çağrılan bir do bloğu alır; geçici (var olmayan) bir `path` ve `path`'e yazılabilen çeşitli argüman türlerine dönüştürülebilen `arg` ile birlikte. İsteğe bağlı `type` argümanı verilirse, do bloğu yalnızca o türde argüman üreten yazıcılar için çağrılır.

Do bloğuna geçirilen `arg`, argüman değerinin kendisi değildir, çünkü bazı test argüman türlerinin her test durumu için başlatılması ve sonlandırılması gerekir. Açık bir dosya tanıtıcısı argümanını düşünün: bir testi kullandıktan sonra, onu tekrar kullanamazsınız; kapatmanız ve bir sonraki test için dosyayı tekrar açmanız gerekir. Bu `arg` fonksiyonu, `@arg_test arg begin ... end` kullanılarak bir `ArgWrite` örneğine dönüştürülebilir.

Ayrıca, `arg_readers` gibi bir yol adı alan bir `arg_writers` yöntemi de vardır:

```
arg_writers(path::AbstractString, [ type = ArgWrite ]) do arg::Function
    ## ön test kurulumu ##
    @arg_test arg begin
        # burada `arg :: ArgWrite`
        ## `arg` kullanarak test ##
    end
    ## test sonrası temizlik ##
end
```

Bu yöntem, `tempname()` tarafından üretilen yol adını kullanmak yerine `path`'i belirtmeniz gerektiğinde kullanışlıdır. `path`, `arg_writers`'ın dışından geçirildiği için, bu biçimde do bloğuna bir argüman değildir.
