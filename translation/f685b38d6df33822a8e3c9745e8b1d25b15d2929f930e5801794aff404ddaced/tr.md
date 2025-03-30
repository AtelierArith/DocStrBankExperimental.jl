```
acquire(f, s::Semaphore)
```

Semaphore `s`'den alım yaptıktan sonra `f`'yi çalıştırır ve tamamlandığında veya hata oluştuğunda `release` eder.

Örneğin, aynı anda yalnızca 2 `foo` çağrısının aktif olmasını sağlayan bir do-block biçimi:

```julia
s = Base.Semaphore(2)
@sync for _ in 1:100
    Threads.@spawn begin
        Base.acquire(s) do
            foo()
        end
    end
end
```

!!! compat "Julia 1.8"
    Bu yöntem en az Julia 1.8 gerektirir.

