```
@raw_str -> String
```

İçinde yerleşim ve kaçış olmadan bir ham dize oluşturun. Tek istisna, tırnak işaretlerinin hala kaçırılması gerektiğidir. Ters eğik çizgiler, hem tırnak işaretlerini hem de diğer ters eğik çizgileri kaçırır, ancak yalnızca bir dizi ters eğik çizgi bir alıntı karakterinden önce geliyorsa. Böylece, 2n ters eğik çizgi bir alıntı ile takip edildiğinde n ters eğik çizgi ve literalın sonunu kodlar, 2n+1 ters eğik çizgi bir alıntı ile takip edildiğinde n ters eğik çizgi ve bir alıntı karakterini kodlar.

# Örnekler

```jldoctest
julia> println(raw"\ $x")
\ $x

julia> println(raw"\"")
"

julia> println(raw"\\\"")
\"

julia> println(raw"\\x \\\"")
\\x \"
```
