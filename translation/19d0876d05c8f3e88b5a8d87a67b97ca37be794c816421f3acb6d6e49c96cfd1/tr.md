```
LibGit2.map(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), range::AbstractString="", by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

[`GitRevWalker`](@ref) `walker` kullanarak depo tarihindeki her bir commit üzerinde "yürüyün", `f`'yi yürüyüşteki her bir commit'e uygulayın. Anahtar argümanlar şunlardır:     * `oid`: Yürüyüşe başlamak için commit'in [`GitHash`](@ref). Varsayılan olarak, [`push_head!`](@ref) kullanılır ve dolayısıyla HEAD commit'i ve tüm atalarına başvurulur.     * `range`: `GitHash`'lerin `oid1..oid2` formatındaki bir aralığı. `f`, ikisi arasındaki tüm commit'lere uygulanacaktır.     * `by`: Sıralama yöntemi. Varsayılan sıralama yoktur. Diğer seçenekler, topolojik sıralama (`LibGit2.Consts.SORT_TOPOLOGICAL`), zamana göre ileri sıralama (`LibGit2.Consts.SORT_TIME`, en eski önce) veya zamana göre geri sıralama (`LibGit2.Consts.SORT_REVERSE`, en yeni önce) şeklindedir.     * `rev`: Sıralı düzeni tersine çevirip çevirmeyeceği (örneğin, topolojik sıralama kullanılıyorsa).

# Örnekler

```julia
oids = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.map((oid, repo)->string(oid), walker, by=LibGit2.Consts.SORT_TIME)
end
```

Burada, `LibGit2.map` her bir commit'i `GitRevWalker` kullanarak ziyaret eder ve `GitHash`'ini bulur.
