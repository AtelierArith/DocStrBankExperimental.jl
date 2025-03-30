```
@invokelatest f(args...; kwargs...)
```

[`invokelatest`](@ref) çağırmak için kullanışlı bir yol sağlar. `@invokelatest f(args...; kwargs...)` basitçe `Base.invokelatest(f, args...; kwargs...)` olarak genişletilecektir.

Aşağıdaki sözdizimini de destekler:

  * `@invokelatest x.f` `Base.invokelatest(getproperty, x, :f)` olarak genişletilir
  * `@invokelatest x.f = v` `Base.invokelatest(setproperty!, x, :f, v)` olarak genişletilir
  * `@invokelatest xs[i]` `Base.invokelatest(getindex, xs, i)` olarak genişletilir
  * `@invokelatest xs[i] = v` `Base.invokelatest(setindex!, xs, v, i)` olarak genişletilir

```jldoctest
julia> @macroexpand @invokelatest f(x; kw=kwv)
:(Base.invokelatest(f, x; kw = kwv))

julia> @macroexpand @invokelatest x.f
:(Base.invokelatest(Base.getproperty, x, :f))

julia> @macroexpand @invokelatest x.f = v
:(Base.invokelatest(Base.setproperty!, x, :f, v))

julia> @macroexpand @invokelatest xs[i]
:(Base.invokelatest(Base.getindex, xs, i))

julia> @macroexpand @invokelatest xs[i] = v
:(Base.invokelatest(Base.setindex!, xs, v, i))
```

!!! compat "Julia 1.7"
    Bu makro Julia 1.7 veya daha yenisini gerektirir.


!!! compat "Julia 1.9"
    Julia 1.9'dan önce, bu makro dışa aktarılmamıştı ve `Base.@invokelatest` olarak adlandırılıyordu.


!!! compat "Julia 1.10"
    Ek `x.f` ve `xs[i]` sözdizimi Julia 1.10'u gerektirir.

