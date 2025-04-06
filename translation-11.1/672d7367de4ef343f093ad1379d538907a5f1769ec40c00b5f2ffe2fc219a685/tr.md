```
@printf([io::IO], "%Fmt", args...)
```

`args`'ı C `printf` stil format belirleme dizesi kullanarak yazdırır. İsteğe bağlı olarak, çıktıyı yönlendirmek için ilk argüman olarak bir `IO` geçirilebilir.

# Örnekler

```jldoctest
julia> @printf "Hello %s" "world"
Hello world

julia> @printf "Scientific notation %e" 1.234
Scientific notation 1.234000e+00

julia> @printf "Scientific notation three digits %.3e" 1.23456
Scientific notation three digits 1.235e+00

julia> @printf "Decimal two digits %.2f" 1.23456
Decimal two digits 1.23

julia> @printf "Padded to length 5 %5i" 123
Padded to length 5   123

julia> @printf "Padded with zeros to length 6 %06i" 123
Padded with zeros to length 6 000123

julia> @printf "Use shorter of decimal or scientific %g %g" 1.23 12300000.0
Use shorter of decimal or scientific 1.23 1.23e+07

julia> @printf "Use dynamic width and precision  %*.*f" 10 2 0.12345
Use dynamic width and precision        0.12
```

Formatın sistematik bir belirlemesi için [buraya](https://en.cppreference.com/w/c/io/fprintf) bakın. Ayrıca, yazdırılmak yerine bir `String` olarak sonucu almak için [`@sprintf`](@ref) kullanın.

# Uyarılar

`Inf` ve `NaN`, `%a`, `%A`, `%e`, `%E`, `%f`, `%F`, `%g` ve `%G` bayrakları için tutarlı bir şekilde `Inf` ve `NaN` olarak yazdırılır. Ayrıca, bir kayan nokta sayısı iki olası çıktı dizesinin sayısal değerlerine eşit derecede yakınsa, sıfırdan daha uzak olan çıktı dizesi seçilir.

# Örnekler

```jldoctest
julia> @printf("%f %F %f %F", Inf, Inf, NaN, NaN)
Inf Inf NaN NaN

julia> @printf "%.0f %.1f %f" 0.5 0.025 -0.0078125
0 0.0 -0.007812
```

!!! uyum "Julia 1.8"
    Julia 1.8'den itibaren, `%s` (dize) ve `%c` (karakter) genişlikleri [`textwidth`](@ref) kullanılarak hesaplanır; bu, örneğin sıfır genişliğindeki karakterleri (diakritik işaretler için birleştirici karakterler gibi) göz ardı eder ve belirli "geniş" karakterleri (örneğin, emoji) genişlik `2` olarak kabul eder.


!!! uyum "Julia 1.10"
    `%*s` ve `%0*.*f` gibi dinamik genişlik belirleyicileri Julia 1.10 gerektirir.

