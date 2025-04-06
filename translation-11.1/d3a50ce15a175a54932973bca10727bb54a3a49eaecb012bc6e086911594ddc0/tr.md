```
ArgWrite = Union{AbstractString, AbstractCmd, IO}
```

`ArgWrite` türleri, `arg_write` fonksiyonunun yazılabilir IO handle'larına dönüştürebildiği türlerin birleşimidir, `arg_write`'in geçici bir dosya oluşturarak işlediği `Nothing` hariç. Ayrıntılar için [`arg_write`](@ref) kısmına bakın.
