```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}; kwargs...) -> Bool
```

Açıklamalı commitlerden ([`GitAnnotated`](@ref) nesneleri olarak yakalanmış) `anns` değişikliklerini `repo` deposunun HEAD'ine birleştirir. Anahtar kelime argümanları şunlardır:

  * `merge_opts::MergeOptions = MergeOptions()`: birleştirmenin nasıl yapılacağına dair seçenekler, hızlı ileri almanın izin verilip verilmediği dahil. Daha fazla bilgi için [`MergeOptions`](@ref) kısmına bakın.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: checkout'un nasıl yapılacağına dair seçenekler. Daha fazla bilgi için [`CheckoutOptions`](@ref) kısmına bakın.

`anns` uzak veya yerel dal başlarını referans alabilir. Birleştirme başarılıysa `true`, aksi takdirde `false` döner (örneğin, dalların ortak bir atası olmadığı için birleştirme mümkün değilse).

# Örnekler

```julia
upst_ann = LibGit2.GitAnnotated(repo, "branch/a")

# dalı birleştir
LibGit2.merge!(repo, [upst_ann])
```
