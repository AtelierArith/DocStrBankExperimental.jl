```
LibGit2.count(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

[`GitRevWalker`](@ref) `walker` kullanarak, depo tarihindeki her bir commit üzerinde "yürüyerek", `f` uygulandığında `true` dönen commit sayısını bulun. Anahtar argümanlar şunlardır:     * `oid`: Yürüyüşe başlamak için commitin [`GitHash`](@ref). Varsayılan olarak, [`push_head!`](@ref) kullanılarak HEAD commit'i ve tüm atalarından başlanır.     * `by`: Sıralama yöntemi. Varsayılan olarak sıralama yapılmaz. Diğer seçenekler, topolojik sıralama (`LibGit2.Consts.SORT_TOPOLOGICAL`), zamana göre ileri sıralama (`LibGit2.Consts.SORT_TIME`, en eski önce) veya zamana göre geri sıralama (`LibGit2.Consts.SORT_REVERSE`, en yeni önce) şeklindedir.     * `rev`: Sıralı düzeni tersine çevirip çevirmeyeceği (örneğin, topolojik sıralama kullanılıyorsa).

# Örnekler

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid, repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

`LibGit2.count`, yürüyüş boyunca belirli bir `GitHash` `commit_oid1` ile birlikte commit sayısını bulur, yürüyüşe o commit'ten başlayarak ve zamanla ileriye doğru hareket ederek devam eder. `GitHash` bir commit'e özgü olduğundan, `cnt` `1` olacaktır.
