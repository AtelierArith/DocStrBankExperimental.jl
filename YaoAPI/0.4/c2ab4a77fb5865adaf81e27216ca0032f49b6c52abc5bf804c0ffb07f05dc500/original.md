```
CompositeBlock{D} <: AbstractBlock{D}
```

Abstract supertype which composite blocks will inherit from. Composite blocks are blocks composited from other [`AbstractBlock`](@ref)s, thus it is a `AbstractBlock` as well.

### Required Methods

  * [`apply!`](@ref)
  * [`mat`](@ref)
  * [`occupied_locs`](@ref).
  * [`subblocks`](@ref).
  * [`chsubblocks`](@ref).

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
