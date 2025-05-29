```
PrimitiveBlock{D} <: AbstractBlock{D}
```

Abstract type that all primitive block will subtype from. A primitive block is a concrete block who can not be decomposed into other blocks. All composite block can be decomposed into several primitive blocks.

!!! note
    subtype for primitive block with parameter should implement `hash` and `==` method to enable key value cache.


### Required Methods

  * [`apply!`](@ref)
  * [`mat`](@ref)
  * [`print_block`](@ref)
  * `Base.hash`
  * `Base.:(==)`

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
