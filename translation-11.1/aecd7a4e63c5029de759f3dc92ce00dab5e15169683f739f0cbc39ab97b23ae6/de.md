```
fld(x, y)
```

Größte ganze Zahl, die kleiner oder gleich `x / y` ist. Entspricht `div(x, y, RoundDown)`.

Siehe auch [`div`](@ref), [`cld`](@ref), [`fld1`](@ref).

# Beispiele

```jldoctest
julia> fld(7.3, 5.5)
1.0

julia> fld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) mit eltype Int64:
 -2  -2  -1  -1  -1  0  0  0  1  1  1
```

Da `fld(x, y)` eine streng korrekte Abrundung basierend auf dem wahren Wert von Fließkommazahlen implementiert, können unintuitive Situationen auftreten. Zum Beispiel:

```jldoctest
julia> fld(6.0, 0.1)
59.0
julia> 6.0 / 0.1
60.0
julia> 6.0 / big(0.1)
59.99999999999999666933092612453056361837965690217069245739573412231113406246995
```

Was hier passiert, ist, dass der wahre Wert der Fließkommazahl, die als `0.1` geschrieben ist, leicht größer ist als der numerische Wert 1/10, während `6.0` die Zahl 6 genau darstellt. Daher ist der wahre Wert von `6.0 / 0.1` leicht kleiner als 60. Bei der Division wird dies genau auf `60.0` gerundet, aber `fld(6.0, 0.1)` nimmt immer die Abrundung des wahren Wertes, sodass das Ergebnis `59.0` ist.
