```
handle_message(logger, level, message, _module, group, id, file, line; key1=val1, ...)
```

`logger`'a `level` seviyesinde bir mesaj kaydedin. Mesajın oluşturulduğu mantıksal konum `_module` ve `group` ile, kaynak konumu ise `file` ve `line` ile verilmektedir. `id`, filtreleme sırasında log ifadesini tanımlamak için kullanılacak rastgele bir benzersiz değerdir (tipik olarak bir [`Symbol`](@ref)).
