```
edit(function, [types])
edit(module)
```

Bir fonksiyonun tanımını düzenleyin, isteğe bağlı olarak hangi yöntemin düzenleneceğini belirtmek için bir türler demeti belirtebilirsiniz. Modüller için ana kaynak dosyasını açın. Modülün önce `using` veya `import` ile yüklenmesi gerekir.

!!! compat "Julia 1.1"
    Modüller üzerinde `edit` kullanmak en az Julia 1.1 gerektirir.


Belirtilen satırda dosyanın açılabilmesini sağlamak için önce `InteractiveUtils.define_editor` çağrısını yapmanız gerekebilir.
