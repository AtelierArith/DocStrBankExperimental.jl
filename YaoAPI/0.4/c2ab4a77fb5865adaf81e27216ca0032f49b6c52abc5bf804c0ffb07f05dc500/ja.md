```
CompositeBlock{D} <: AbstractBlock{D}
```

合成ブロックが継承する抽象スーパークラス。合成ブロックは他の [`AbstractBlock`](@ref) から合成されたブロックであり、したがってそれ自体も `AbstractBlock` です。

### 必要なメソッド

  * [`apply!`](@ref)
  * [`mat`](@ref)
  * [`occupied_locs`](@ref).
  * [`subblocks`](@ref).
  * [`chsubblocks`](@ref).

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
