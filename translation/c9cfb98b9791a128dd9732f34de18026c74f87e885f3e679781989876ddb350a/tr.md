```
@noinline
```

Derleyiciye bir fonksiyonu iç içe geçirmemesi gerektiğini belirtir.

Küçük fonksiyonlar genellikle otomatik olarak iç içe geçirilir. Küçük fonksiyonlar üzerinde `@noinline` kullanarak otomatik iç içe geçirme engellenebilir.

`@noinline`, bir fonksiyon tanımının hemen öncesinde veya bir fonksiyon gövdesi içinde uygulanabilir.

```julia
# uzun tanım için not ekle
@noinline function longdef(x)
    ...
end

# kısa tanım için not ekle
@noinline shortdef(x) = ...

# bir `do` bloğunun oluşturduğu anonim fonksiyona not ekle
f() do
    @noinline
    ...
end
```

!!! uyum "Julia 1.8"
    Bir fonksiyon gövdesi içindeki kullanım en az Julia 1.8 gerektirir.


---

```
@noinline block
```

Derleyiciye `block` içindeki çağrıları iç içe geçirmemesi gerektiğini belirtir.

```julia
# Derleyici `f`'yi iç içe geçirmemeye çalışacak
@noinline f(...)

# Derleyici `f`, `g` ve `+`'yı iç içe geçirmemeye çalışacak
@noinline f(...) + g(...)
```

!!! not
    Bir çağrı yeri notu, çağrılan fonksiyonun tanımına uygulanan nottan her zaman önceliklidir:

    ```julia
    @inline function explicit_inline(args...)
        # gövde
    end

    let
        @noinline explicit_inline(args...) # iç içe geçirilmeyecek
    end
    ```


!!! not
    İç içe geçmiş çağrı yeri notları olduğunda, en içteki not önceliklidir:

    ```julia
    @inline let a0, b0 = ...
        a = @noinline f(a0)  # derleyici bu çağrıyı iç içe geçirmeyecek
        b = f(b0)            # derleyici bu çağrıyı iç içe geçirmeye çalışacak
        return a, b
    end
    ```


!!! uyum "Julia 1.8"
    Çağrı yeri notu en az Julia 1.8 gerektirir.


---

!!! not
    Fonksiyon basit ise (örneğin bir sabit döndürüyorsa) yine de iç içe geçirilebilir.

