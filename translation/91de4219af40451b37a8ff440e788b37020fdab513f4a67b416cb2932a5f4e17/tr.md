```
map(f, A::AbstractArray...) -> N-dizi
```

Aynı [`ndims`](@ref) boyutlarına sahip çok boyutlu diziler üzerinde işlem yaparken, hepsinin aynı [`axes`](@ref) boyutlarına sahip olması gerekir ve sonuç da öyle olacaktır.

Ayrıca, boyutları uyuşmayan dizilere izin veren [`broadcast`](@ref) fonksiyonuna da bakın.

# Örnekler

```
julia> map(//, [1 2; 3 4], [4 3; 2 1])
2×2 Matris{Rasyonel{Int64}}:
 1//4  2//3
 3//2  4//1

julia> map(+, [1 2; 3 4], zeros(2,1))
HATA: BoyutUyumsuzluğu

julia> map(+, [1 2; 3 4], [1,10,100,1000], zeros(3,1))  # 3. dizi tükenene kadar iterasyon yapar
3-elemanlı Vektör{Float64}:
   2.0
  13.0
 102.0
```
