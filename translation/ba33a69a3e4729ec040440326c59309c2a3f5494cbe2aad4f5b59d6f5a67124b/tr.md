```
@inline
```

Derleyiciye bu fonksiyonun inline edilmesinin değerli olduğunu belirtir.

Küçük fonksiyonlar genellikle `@inline` anotasyonuna ihtiyaç duymaz, çünkü derleyici bunu otomatik olarak yapar. Daha büyük fonksiyonlarda `@inline` kullanarak, derleyiciye inline etmesi için ekstra bir teşvik verilebilir.

`@inline`, bir fonksiyon tanımının hemen öncesinde veya bir fonksiyon gövdesi içinde uygulanabilir.

```julia
# uzun tanımı anotasyonla
@inline function longdef(x)
    ...
end

# kısa tanımı anotasyonla
@inline shortdef(x) = ...

# bir `do` bloğu oluşturan anonim fonksiyonu anotasyonla
f() do
    @inline
    ...
end
```

!!! compat "Julia 1.8"
    Bir fonksiyon gövdesi içindeki kullanım en az Julia 1.8 gerektirir.


---

```
@inline block
```

Derleyiciye `block` içindeki çağrıların inline edilmesinin değerli olduğunu belirtir.

```julia
# Derleyici `f`'yi inline etmeye çalışacak
@inline f(...)

# Derleyici `f`, `g` ve `+`'yı inline etmeye çalışacak
@inline f(...) + g(...)
```

!!! note
    Bir çağrı yeri anotasyonu, çağrılan fonksiyonun tanımına uygulanan anotasyondan her zaman önceliklidir:

    ```julia
    @noinline function explicit_noinline(args...)
        # gövde
    end

    let
        @inline explicit_noinline(args...) # inline edilecek
    end
    ```


!!! note
    İç içe geçmiş çağrı yeri anotasyonları olduğunda, en içteki anotasyon önceliklidir:

    ```julia
    @noinline let a0, b0 = ...
        a = @inline f(a0)  # derleyici bu çağrıyı inline etmeye çalışacak
        b = f(b0)          # derleyici bu çağrıyı inline etmeye çalışmayacak
        return a, b
    end
    ```


!!! warning
    Bir çağrı yeri anotasyonu, maliyet modeline bakılmaksızın inline etmeyi zorlamaya çalışsa da, bunun başarılı olamayacağı durumlar hala vardır. Özellikle, özyinelemeli çağrılar `@inline` ile anotasyonlu olsalar bile inline edilemezler.


!!! compat "Julia 1.8"
    Çağrı yeri anotasyonu en az Julia 1.8 gerektirir.

