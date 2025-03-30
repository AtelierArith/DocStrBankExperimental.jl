```
base64encode(writefunc, args...; context=nothing)
base64encode(args...; context=nothing)
```

Bir [`write`](@ref)-benzeri fonksiyon `writefunc` verildiğinde, ilk argümanı bir I/O akışı olan `base64encode(writefunc, args...)`, `args...`'ı base64 kodlu bir dizeye yazmak için `writefunc`'ı çağırır ve dizeyi döner. `base64encode(args...)`, `base64encode(write, args...)` ile eşdeğerdir: argümanlarını standart [`write`](@ref) fonksiyonlarını kullanarak baytlara dönüştürür ve base64 kodlu dizeyi döner.

İsteğe bağlı anahtar argümanı `context`, `writefunc` veya `write`'a geçirilen I/O akışı için kullanılan özelliklere sahip bir `IO` veya [`IOContext`](@ref) nesnesi ya da `:key=>value` çiftine ayarlanabilir.

Ayrıca bkz. [`base64decode`](@ref).
