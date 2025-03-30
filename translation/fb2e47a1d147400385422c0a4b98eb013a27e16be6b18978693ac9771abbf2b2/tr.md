```
@invoke f(arg::T, ...; kwargs...)
```

[`invoke`](@ref) çağrısını yapmak için pratik bir yol sağlar ve `@invoke f(arg1::T1, arg2::T2; kwargs...)` ifadesini `invoke(f, Tuple{T1,T2}, arg1, arg2; kwargs...)` şeklinde genişletir. Bir argümanın türü belirtilmediğinde, bu argümanın `Core.Typeof` ile değiştirilir. Bir argümanın türü belirtilmemiş veya açıkça `Any` olarak tanımlanmış bir yöntemi çağırmak için, argümanı `::Any` ile anotlayın.

Aşağıdaki sözdizimini de destekler:

  * `@invoke (x::X).f` ifadesi `invoke(getproperty, Tuple{X,Symbol}, x, :f)` şeklinde genişletilir.
  * `@invoke (x::X).f = v::V` ifadesi `invoke(setproperty!, Tuple{X,Symbol,V}, x, :f, v)` şeklinde genişletilir.
  * `@invoke (xs::Xs)[i::I]` ifadesi `invoke(getindex, Tuple{Xs,I}, xs, i)` şeklinde genişletilir.
  * `@invoke (xs::Xs)[i::I] = v::V` ifadesi `invoke(setindex!, Tuple{Xs,V,I}, xs, v, i)` şeklinde genişletilir.

# Örnekler

```jldoctest
julia> @macroexpand @invoke f(x::T, y)
:(Core.invoke(f, Tuple{T, Core.Typeof(y)}, x, y))

julia> @invoke 420::Integer % Unsigned
0x00000000000001a4

julia> @macroexpand @invoke (x::X).f
:(Core.invoke(Base.getproperty, Tuple{X, Core.Typeof(:f)}, x, :f))

julia> @macroexpand @invoke (x::X).f = v::V
:(Core.invoke(Base.setproperty!, Tuple{X, Core.Typeof(:f), V}, x, :f, v))

julia> @macroexpand @invoke (xs::Xs)[i::I]
:(Core.invoke(Base.getindex, Tuple{Xs, I}, xs, i))

julia> @macroexpand @invoke (xs::Xs)[i::I] = v::V
:(Core.invoke(Base.setindex!, Tuple{Xs, V, I}, xs, v, i))
```

!!! compat "Julia 1.7"
    Bu makro Julia 1.7 veya daha yenisini gerektirir.


!!! compat "Julia 1.9"
    Bu makro Julia 1.9 itibarıyla dışa aktarılmıştır.


!!! compat "Julia 1.10"
    Ek sözdizimi Julia 1.10 itibarıyla desteklenmektedir.

