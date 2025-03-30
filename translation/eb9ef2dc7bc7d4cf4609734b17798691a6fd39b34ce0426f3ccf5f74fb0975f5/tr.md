```
GC.@preserve x1 x2 ... xn expr
```

`x1, x2, ...` nesnelerini `expr` ifadesinin değerlendirilmesi sırasında *kullanımda* olarak işaretler. Bu, yalnızca `expr`'nin `x`'lerden birine ait olan bellek veya diğer kaynakları *dolaylı olarak kullandığı* durumlarda güvenli olmayan kodda gereklidir.

`x`'nin *dolaylı kullanımı*, derleyicinin göremediği `x`'ye mantıksal olarak ait olan kaynakların herhangi bir dolaylı kullanımını kapsar. Bazı örnekler:

  * Bir `Ptr` aracılığıyla bir nesnenin belleğine doğrudan erişim
  * `x`'ye bir işaretçi geçirme `ccall`'e
  * `x`'nin kaynaklarını kullanma, bunlar sonlandırıcıda temizlenecektir.

`@preserve` genellikle nesne ömrünü kısaca uzattığı tipik kullanım durumlarında herhangi bir performans etkisi olmamalıdır. Uygulamada, `@preserve` dinamik olarak tahsis edilen nesneleri çöp toplama işlemlerinden korumak gibi etkileri vardır.

# Örnekler

`unsafe_load` ile bir işaretçiden yükleme yaparken, temel nesne dolaylı olarak kullanılır; örneğin `unsafe_load(p)` ifadesinde `x` dolaylı olarak kullanılır:

```jldoctest
julia> let
           x = Ref{Int}(101)
           p = Base.unsafe_convert(Ptr{Int}, x)
           GC.@preserve x unsafe_load(p)
       end
101
```

`ccall`'e işaretçi geçerken, işaret edilen nesne dolaylı olarak kullanılır ve korunmalıdır. (Ancak, genellikle `x`'yi doğrudan `ccall`'e geçirmeniz gerektiğini unutmayın; bu, açık bir kullanım olarak sayılır.)

```jldoctest
julia> let
           x = "Hello"
           p = pointer(x)
           Int(GC.@preserve x @ccall strlen(p::Cstring)::Csize_t)
           # Tercih edilen alternatif
           Int(@ccall strlen(x::Cstring)::Csize_t)
       end
5
```
