```
log(b,x)
```

`x`'in taban `b` logaritmasını hesaplar. Negatif [`Real`](@ref) argümanlar için [`DomainError`](@ref) fırlatır.

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(4,8)
1.5

julia> log(4,2)
0.5

julia> log(-2, 3)
HATA: -2.0 ile DomainError:
log negatif bir gerçek argüman ile çağrıldı, ancak karmaşık bir argüman ile çağrıldığında yalnızca karmaşık bir sonuç döndürecektir. log(Complex(x))'i deneyin.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(2, -3)
HATA: -3.0 ile DomainError:
log negatif bir gerçek argüman ile çağrıldı, ancak karmaşık bir argüman ile çağrıldığında yalnızca karmaşık bir sonuç döndürecektir. log(Complex(x))'i deneyin.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```

!!! not
    Eğer `b` 2 veya 10'un bir kuvvetiyse, [`log2`](@ref) veya [`log10`](@ref) kullanılmalıdır, çünkü bunlar genellikle daha hızlı ve daha doğru olacaktır. Örneğin,

    ```jldoctest
    julia> log(100,1000000)
    2.9999999999999996

    julia> log10(1000000)/2
    3.0
    ```

