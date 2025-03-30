```
extrema(f, itr; [init]) -> (mn, mx)
```

`itr`'deki her bir elemana uygulanan `f`'nin hem minimum `mn` hem de maksimum `mx` değerlerini hesaplayın ve bunları 2-tuple olarak döndürün. `itr` üzerinde yalnızca bir geçiş yapılır.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, `min` ve `max` için nötr elemanlar olan bir 2-tuple olmalıdır (yani, diğer herhangi bir elemandan büyük/küçük veya eşit olan). Bu, boş olmayan koleksiyonlar için kullanılır. Not: Bu, boş `itr` için döndürülen değerin `(mn, mx)`'nin `mn ≥ mx` koşulunu sağladığını, oysa boş olmayan `itr` için `mn ≤ mx` koşulunu sağladığını ima eder. Bu "paradoksal" ama yine de beklenen bir sonuçtur.

!!! compat "Julia 1.2"
    Bu yöntem Julia 1.2 veya daha yenisini gerektirir.


!!! compat "Julia 1.8"
    Anahtar argüman `init`, Julia 1.8 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> extrema(sin, 0:π)
(0.0, 0.9092974268256817)

julia> extrema(sin, Real[]; init = (1.0, -1.0))  # iyi, çünkü -1 ≤ sin(::Real) ≤ 1
(1.0, -1.0)
```
