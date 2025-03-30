```
@fastmath expr
```

Dönüştürülmüş bir ifadenin yürütülmesini sağlar; bu, katı IEEE semantiğini ihlal edebilecek işlevleri çağırır. Bu, mümkün olan en hızlı işlemi sağlar, ancak sonuçlar belirsizdir – bunu yaparken dikkatli olun, çünkü sayısal sonuçları değiştirebilir.

Bu, [LLVM Fast-Math bayraklarını](https://llvm.org/docs/LangRef.html#fast-math-flags) ayarlar ve clang'daki `-ffast-math` seçeneğine karşılık gelir. Daha fazla ayrıntı için [performans notları](@ref man-performance-annotations) bölümüne bakın.

# Örnekler

```jldoctest
julia> @fastmath 1+2
3

julia> @fastmath(sin(3))
0.1411200080598672
```
