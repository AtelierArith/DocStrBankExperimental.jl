```
AbstractContainer{BT,D} <: CompositeBlock{D}
```

Abstract type for container block. Container blocks are blocks contain a single block.

### Required Methods

  * [`apply!`](@ref)
  * [`mat`](@ref)
  * [`content`](@ref)
  * [`chcontent`](@ref)
  * [`occupied_locs`](@ref).

### Optional Methods

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
