```
@inferred [AllowedType] f(x)
```

Prueba que la expresión de llamada `f(x)` devuelve un valor del mismo tipo inferido por el compilador. Es útil para verificar la estabilidad de tipos.

`f(x)` puede ser cualquier expresión de llamada. Devuelve el resultado de `f(x)` si los tipos coinciden, y un `Error` `Result` si encuentra tipos diferentes.

Opcionalmente, `AllowedType` relaja la prueba, haciéndola pasar cuando el tipo de `f(x)` coincide con el tipo inferido módulo `AllowedType`, o cuando el tipo de retorno es un subtipo de `AllowedType`. Esto es útil al probar la estabilidad de tipos de funciones que devuelven una pequeña unión como `Union{Nothing, T}` o `Union{Missing, T}`.

```jldoctest; setup = :(using InteractiveUtils; using Base: >), filter = r"begin\n(.|\n)*end"
julia> f(a) = a > 1 ? 1 : 1.0
f (generic function with 1 method)

julia> typeof(f(2))
Int64

julia> @code_warntype f(2)
MethodInstance for f(::Int64)
  from f(a) @ Main none:1
Arguments
  #self#::Core.Const(f)
  a::Int64
Body::UNION{FLOAT64, INT64}
1 ─ %1 = (a > 1)::Bool
└──      goto #3 if not %1
2 ─      return 1
3 ─      return 1.0

julia> @inferred f(2)
ERROR: el tipo de retorno Int64 no coincide con el tipo de retorno inferido Union{Float64, Int64}
[...]

julia> @inferred max(1, 2)
2

julia> g(a) = a < 10 ? missing : 1.0
g (generic function with 1 method)

julia> @inferred g(20)
ERROR: el tipo de retorno Float64 no coincide con el tipo de retorno inferido Union{Missing, Float64}
[...]

julia> @inferred Missing g(20)
1.0

julia> h(a) = a < 10 ? missing : f(a)
h (generic function with 1 method)

julia> @inferred Missing h(20)
ERROR: el tipo de retorno Int64 no coincide con el tipo de retorno inferido Union{Missing, Float64, Int64}
[...]
```
