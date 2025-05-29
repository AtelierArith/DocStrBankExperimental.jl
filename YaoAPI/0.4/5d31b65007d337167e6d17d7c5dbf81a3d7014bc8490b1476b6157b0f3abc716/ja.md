```
AbstractContainer{BT,D} <: CompositeBlock{D}
```

コンテナブロックの抽象型。コンテナブロックは、単一のブロックを含むブロックです。

### 必要なメソッド

  * [`apply!`](@ref)
  * [`mat`](@ref)
  * [`content`](@ref)
  * [`chcontent`](@ref)
  * [`occupied_locs`](@ref).

### オプションのメソッド

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
