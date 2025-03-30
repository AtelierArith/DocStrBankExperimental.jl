```
stack(f, args...; [dims])
```

Bir koleksiyonun her bir elemanına bir fonksiyon uygulayın ve sonucu `stack` edin. Veya birden fazla koleksiyonu, [`zip`](@ref) ile birleştirerek.

Fonksiyon, hepsi aynı boyutta olan diziler (veya demetler, veya diğer iteratörler) döndürmelidir. Bunlar, sonuçların dilimlerini oluşturur ve her biri `dims` (verilmişse) veya varsayılan olarak son boyutlar boyunca ayrılır.

Ayrıca [`mapslices`](@ref), [`eachcol`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> stack(c -> (c, c-32), "julia")
2×5 Matrix{Char}:
 'j'  'u'  'l'  'i'  'a'
 'J'  'U'  'L'  'I'  'A'

julia> stack(eachrow([1 2 3; 4 5 6]), (10, 100); dims=1) do row, n
         vcat(row, row .* n, row ./ n)
       end
2×9 Matrix{Float64}:
 1.0  2.0  3.0   10.0   20.0   30.0  0.1   0.2   0.3
 4.0  5.0  6.0  400.0  500.0  600.0  0.04  0.05  0.06
```
