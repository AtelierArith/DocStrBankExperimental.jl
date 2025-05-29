```
PrimitiveBlock{D} <: AbstractBlock{D}
```

すべてのプリミティブブロックがサブタイプとなる抽象型。プリミティブブロックは、他のブロックに分解できない具体的なブロックです。すべてのコンポジットブロックは、いくつかのプリミティブブロックに分解できます。

!!! note
    パラメータを持つプリミティブブロックのサブタイプは、キー値キャッシュを有効にするために `hash` と `==` メソッドを実装する必要があります。


### 必要なメソッド

  * [`apply!`](@ref)
  * [`mat`](@ref)
  * [`print_block`](@ref)
  * `Base.hash`
  * `Base.:(==)`

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
