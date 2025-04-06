```
replace([io::IO], s::AbstractString, pat=>r, [pat2=>r2, ...]; [count::Integer])
```

Verilen `pat` desenini `s` içinde arayın ve her bir örneği `r` ile değiştirin. Eğer `count` sağlanmışsa, en fazla `count` örneği değiştirilir. `pat` tek bir karakter, bir vektör veya karakterler kümesi, bir dize veya bir düzenli ifade olabilir. Eğer `r` bir fonksiyonsa, her bir örnek `r(s)` ile değiştirilir; burada `s`, eşleşen alt dizedir (eğer `pat` bir `AbstractPattern` veya `AbstractString` ise) veya karakterdir (eğer `pat` bir `AbstractChar` veya bir `AbstractChar` koleksiyonu ise). Eğer `pat` bir düzenli ifade ise ve `r` bir [`SubstitutionString`](@ref) ise, o zaman `r` içindeki yakalama grubu referansları, karşılık gelen eşleşen metin ile değiştirilir. `pat` örneklerini `string`'den kaldırmak için, `r`'yi boş `String` (`""`) olarak ayarlayın.

Dönüş değeri, değişikliklerden sonra yeni bir dizedir. Eğer `io::IO` argümanı sağlanmışsa, dönüştürülmüş dize bunun yerine `io`'ya yazılır (dönüş `io` olur). (Örneğin, bu, önceden tahsis edilmiş bir tampon dizisini yerinde yeniden kullanmak için bir [`IOBuffer`](@ref) ile birlikte kullanılabilir.)

Birden fazla desen belirtilebilir ve bunlar soldan sağa aynı anda uygulanır, bu nedenle yalnızca bir desen herhangi bir karaktere uygulanır ve desenler yalnızca giriş metnine, değişikliklere değil, uygulanır.

!!! compat "Julia 1.7"
    Birden fazla desen desteği 1.7 sürümünü gerektirir.


!!! compat "Julia 1.10"
    `io::IO` argümanı 1.10 sürümünü gerektirir.


# Örnekler

```jldoctest
julia> replace("Python is a programming language.", "Python" => "Julia")
"Julia is a programming language."

julia> replace("The quick foxes run quickly.", "quick" => "slow", count=1)
"The slow foxes run quickly."

julia> replace("The quick foxes run quickly.", "quick" => "", count=1)
"The  foxes run quickly."

julia> replace("The quick foxes run quickly.", r"fox(es)?" => s"bus\1")
"The quick buses run quickly."

julia> replace("abcabc", "a" => "b", "b" => "c", r".+" => "a")
"bca"
```
