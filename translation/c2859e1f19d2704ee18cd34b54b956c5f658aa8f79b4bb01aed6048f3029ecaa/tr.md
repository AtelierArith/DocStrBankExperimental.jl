```
finalizer(f, x)
```

Bir `f(x)` fonksiyonunu, `x` için program erişimine kapalı referanslar kalmadığında çağrılacak şekilde kaydedin ve `x`'i döndürün. `x`'in tipi `mutable struct` olmalıdır, aksi takdirde fonksiyon bir hata fırlatır.

`f`, bir görev değişimi yaratmamalıdır, bu da `println` gibi çoğu G/Ç işlemini hariç tutar. (finalizer'ın dışındaki bağlam değişimini ertelemek için) `@async` makrosunu kullanmak veya C'deki G/Ç fonksiyonlarını doğrudan çağırmak için `ccall` kullanmak, hata ayıklama amaçları için faydalı olabilir.

`f`'nin yürütülmesi için garanti edilen bir dünya yaşı yoktur. `f`, finalizer'ın kaydedildiği dünya yaşında veya daha sonraki herhangi bir dünya yaşında çağrılabilir.

# Örnekler

```julia
finalizer(my_mutable_struct) do x
    @async println("Finalizing $x.")
end

finalizer(my_mutable_struct) do x
    ccall(:jl_safe_printf, Cvoid, (Cstring, Cstring), "Finalizing %s.", repr(x))
end
```

Bir finalizer, nesne oluşturulurken kaydedilebilir. Aşağıdaki örnekte, finalizer'ın yeni oluşturulan `mutable struct` `x`'i döndürmesini dolaylı olarak sağladığımıza dikkat edin.

```julia
mutable struct MyMutableStruct
    bar
    function MyMutableStruct(bar)
        x = new(bar)
        f(t) = @async println("Finalizing $t.")
        finalizer(f, x)
    end
end
```
