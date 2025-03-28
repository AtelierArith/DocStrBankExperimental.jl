```
log(b,x)
```

Calcula el logaritmo de `x` en base `b`. Lanza [`DomainError`](@ref) para argumentos [`Real`](@ref) negativos.

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(4,8)
1.5

julia> log(4,2)
0.5

julia> log(-2, 3)
ERROR: DomainError with -2.0:
log fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(2, -3)
ERROR: DomainError with -3.0:
log fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```

!!! nota
    Si `b` es una potencia de 2 o 10, se deben usar [`log2`](@ref) o [`log10`](@ref), ya que estos serán típicamente más rápidos y precisos. Por ejemplo,

    ```jldoctest
    julia> log(100,1000000)
    2.9999999999999996

    julia> log10(1000000)/2
    3.0
    ```

