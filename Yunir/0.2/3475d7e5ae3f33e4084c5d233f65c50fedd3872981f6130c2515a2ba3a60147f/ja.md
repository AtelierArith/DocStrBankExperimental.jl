```
isfeat(x::Orthography, y::Type{<:AbstractConsonant})
```

は、xがyの特徴であるかどうかをチェックします。

```julia-repl
julia> ar_basmala = "بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ";
julia> arb_token = tokenize(ar_basmala)
4-element Vector{String}:
 "بِسْمِ"
 "ٱللَّهِ"
 "ٱلرَّحْمَٰنِ"
 "ٱلرَّحِيمِ"
julia> arb_parsed2 = parse.(Orthography, arb_token)
4-element Vector{Orthography}:
 Orthography(Type[Ba, Kasra, Seen, Sukun, Meem, Kasra])
 Orthography(Type[AlifHamzatWasl, Lam, Lam, Shadda, Fatha, Ha, Kasra])
 Orthography(Type[AlifHamzatWasl, Lam, Ra, Shadda, Fatha, HHa, Sukun, Meem, Fatha, AlifKhanjareeya, Noon, Kasra])
 Orthography(Type[AlifHamzatWasl, Lam, Ra, Shadda, Fatha, HHa, Kasra, Ya, Meem, Kasra])
julia> isfeat(arb_parsed2[1], AbstractLunar)
6-element BitVector:
 1
 0
 0
 0
 1
 0
```
