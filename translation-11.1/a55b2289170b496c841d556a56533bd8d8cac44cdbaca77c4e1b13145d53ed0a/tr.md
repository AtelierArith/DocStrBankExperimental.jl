```
LibGit2.push!(w::GitRevWalker, cid::GitHash)
```

[`GitRevWalker`](@ref) `walker`'ı `cid` commit'inde başlatın. Bu fonksiyon, belirli bir yıl itibarıyla tüm commit'lere bir fonksiyon uygulamak için kullanılabilir; bu, o yılın ilk commit'ini `cid` olarak geçirip ardından elde edilen `w`'yi [`LibGit2.map`](@ref) fonksiyonuna geçirerek yapılır.
