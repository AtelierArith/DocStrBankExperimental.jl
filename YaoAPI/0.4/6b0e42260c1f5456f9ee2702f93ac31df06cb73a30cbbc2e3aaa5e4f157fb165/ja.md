```
AbstractBlock{D}
```

量子回路ブロックのための抽象型。`D`は各クディットのレベル数です。

### 必要なメソッド

  * [`apply!`](@ref).
  * [`mat`](@ref).
  * [`occupied_locs`](@ref).
  * [`print_block`](@ref)

### オプションのメソッド

  * [`content`](@ref)
  * [`chcontent`](@ref)
  * [`subblocks`](@ref).
  * [`chsubblocks`](@ref).
  * `Base.hash`
  * `Base.:(==)`
  * [`nlevel`](@ref).
  * [`getiparams`](@ref).
  * [`setiparams!`](@ref).
  * [`parameters`](@ref).
  * [`nparameters`](@ref).
  * [`iparams_eltype`](@ref).
  * [`parameters_eltype`](@ref).
  * [`dispatch!`](@ref).
  * [`render_params`](@ref).
  * [`apply_back!`](@ref).
  * [`mat_back!`](@ref).
