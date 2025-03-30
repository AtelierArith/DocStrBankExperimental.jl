```
Profile.Allocs.@profile [örnek_oranı=0.1] expr
```

`expr` sırasında gerçekleşen profil tahsisatlarını profil alır, hem sonucu hem de AllocResults yapısını döndürür.

1.0'lık bir örnek oranı her şeyi kaydedecektir; 0.0 hiçbir şeyi kaydetmeyecektir.

```julia
julia> Profile.Allocs.@profile örnek_oranı=0.01 peakflops()
1.03733270279065e11

julia> sonuçlar = Profile.Allocs.fetch()

julia> last(sort(sonuçlar.allocs, by=x->x.size))
Profile.Allocs.Alloc(Vector{Any}, Base.StackTraces.StackFrame[_new_array_ at array.c:127, ...], 5576)
```

Daha fazla bilgi için Julia belgelerindeki profil alma kılavuzuna bakın.

!!! uyumluluk "Julia 1.11"
    Daha eski Julia sürümleri tüm durumlarda türleri yakalayamazdı. Daha eski Julia sürümlerinde, `Profile.Allocs.UnknownType` türünde bir tahsisat görüyorsanız, bu, profilcinin tahsis edilen nesnenin türünü bilmediği anlamına gelir. Bu, esasen tahsisatın derleyici tarafından üretilen oluşturulmuş koddan geldiği durumlarda meydana geldi. Daha fazla bilgi için [sorun #43688](https://github.com/JuliaLang/julia/issues/43688) sayfasına bakın.

    Julia 1.11'den itibaren, tüm tahsisatların bir türü bildirilmelidir.


!!! uyumluluk "Julia 1.8"
    Tahsisat profilcisi Julia 1.8'de eklendi.

