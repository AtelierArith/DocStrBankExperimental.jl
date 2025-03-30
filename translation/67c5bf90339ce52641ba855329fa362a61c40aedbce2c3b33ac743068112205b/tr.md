```
^(x, y)
```

Üst alma operatörü.

Eğer `x` ve `y` tam sayılar ise, sonuç taşabilir. Bilimsel notasyonda sayılar girmek için `1.2 * 10^3` yerine [`Float64`](@ref) literalleri olan `1.2e3` kullanın.

Eğer `y` bir `Int` literali ise (örneğin `x^2`'deki `2` veya `x^-3`'deki `-3`), Julia kodu `x^y`, derleyici tarafından `Base.literal_pow(^, x, Val(y))`'ye dönüştürülür; bu, üssün değerine göre derleme zamanı uzmanlaşmasını sağlar. (Varsayılan bir geri dönüş olarak `Base.literal_pow(^, x, Val(y)) = ^(x,y)` vardır; burada genellikle `^ == Base.^`'dir, aksi takdirde `^` çağrılan ad alanında tanımlanmışsa farklı olabilir.) Eğer `y` negatif bir tam sayı literali ise, o zaman `Base.literal_pow` işlemi varsayılan olarak `inv(x)^-y`'ye dönüştürülür; burada `-y` pozitif bir değerdir.

Ayrıca [`exp2`](@ref), [`<<`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> 3^5
243

julia> 3^-1  # Base.literal_pow kullanır
0.3333333333333333

julia> p = -1;

julia> 3^p
HATA: -1 ile DomainError:
Bir tam sayıyı negatif bir üste -1 yükseltmek mümkün değil.
[...]

julia> 3.0^p
0.3333333333333333

julia> 10^19 > 0  # tam sayı taşması
false

julia> big(10)^19 == 1e19
true
```
