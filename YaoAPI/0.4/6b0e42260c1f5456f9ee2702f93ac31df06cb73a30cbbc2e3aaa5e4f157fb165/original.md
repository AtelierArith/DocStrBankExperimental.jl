```
AbstractBlock{D}
```

Abstract type for quantum circuit blocks. while `D` is the number level in each qudit.

### Required Methods

  * [`apply!`](@ref).
  * [`mat`](@ref).
  * [`occupied_locs`](@ref).
  * [`print_block`](@ref)

### Optional Methods

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
