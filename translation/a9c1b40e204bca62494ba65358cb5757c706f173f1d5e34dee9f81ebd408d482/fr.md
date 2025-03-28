```
@inferred [AllowedType] f(x)
```

Teste que l'expression d'appel `f(x)` renvoie une valeur du même type que celui inféré par le compilateur. Il est utile de vérifier la stabilité des types.

`f(x)` peut être n'importe quelle expression d'appel. Renvoie le résultat de `f(x)` si les types correspondent, et un `Error` `Result` s'il trouve des types différents.

En option, `AllowedType` assouplit le test, en le faisant réussir lorsque soit le type de `f(x)` correspond au type inféré modulo `AllowedType`, soit lorsque le type de retour est un sous-type de `AllowedType`. Cela est utile lors des tests de stabilité des types de fonctions renvoyant une petite union telle que `Union{Nothing, T}` ou `Union{Missing, T}`.

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
ERROR: return type Int64 does not match inferred return type Union{Float64, Int64}
[...]

julia> @inferred max(1, 2)
2

julia> g(a) = a < 10 ? missing : 1.0
g (generic function with 1 method)

julia> @inferred g(20)
ERROR: return type Float64 does not match inferred return type Union{Missing, Float64}
[...]

julia> @inferred Missing g(20)
1.0

julia> h(a) = a < 10 ? missing : f(a)
h (generic function with 1 method)

julia> @inferred Missing h(20)
ERROR: return type Int64 does not match inferred return type Union{Missing, Float64, Int64}
[...]
```
