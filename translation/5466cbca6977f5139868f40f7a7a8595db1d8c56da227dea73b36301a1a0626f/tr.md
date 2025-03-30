```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}, fastforward::Bool; kwargs...) -> Bool
```

Açıklamalı commitlerden ([`GitAnnotated`](@ref) nesneleri olarak yakalanmış) `anns` değişikliklerini `repo` deposunun HEAD'ine birleştirir. Eğer `fastforward` `true` ise, *sadece* hızlı birleştirme yapılmasına izin verilir. Bu durumda, eğer çatışmalar meydana gelirse, birleştirme başarısız olacaktır. Aksi takdirde, eğer `fastforward` `false` ise, birleştirme, kullanıcının çözmesi gereken bir çatışma dosyası üretebilir.

Anahtar argümanlar şunlardır:

  * `merge_opts::MergeOptions = MergeOptions()`: birleştirmenin nasıl yapılacağına dair seçenekler, hızlı birleştirmenin izin verilip verilmediği dahil. Daha fazla bilgi için [`MergeOptions`](@ref) kısmına bakın.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: checkout'un nasıl yapılacağına dair seçenekler. Daha fazla bilgi için [`CheckoutOptions`](@ref) kısmına bakın.

`anns` uzaktan veya yerel dal başlarına atıfta bulunabilir. Birleştirme başarılı olursa `true`, aksi takdirde `false` döner (örneğin, dalların ortak bir atası olmadığı için birleştirme mümkün değilse).

# Örnekler

```julia
upst_ann_1 = LibGit2.GitAnnotated(repo, "branch/a")

# dalı birleştir, hızlı birleştir
LibGit2.merge!(repo, [upst_ann_1], true)

# birleştirme çatışmaları!
upst_ann_2 = LibGit2.GitAnnotated(repo, "branch/b")
# dalı birleştir, hızlı birleştirmeyi dene
LibGit2.merge!(repo, [upst_ann_2], true) # false dönecek
LibGit2.merge!(repo, [upst_ann_2], false) # true dönecek
```
