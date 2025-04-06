```
@inferred [ErlaubterTyp] f(x)
```

Testet, ob der Aufrufausdruck `f(x)` einen Wert des gleichen Typs zurückgibt, der vom Compiler abgeleitet wurde. Es ist nützlich, um die Typstabilität zu überprüfen.

`f(x)` kann jeder Aufrufausdruck sein. Gibt das Ergebnis von `f(x)` zurück, wenn die Typen übereinstimmen, und ein `Error` `Result`, wenn unterschiedliche Typen gefunden werden.

Optional lockert `ErlaubterTyp` den Test, indem er besteht, wenn entweder der Typ von `f(x)` mit dem abgeleiteten Typ modulo `ErlaubterTyp` übereinstimmt oder wenn der Rückgabetyp ein Subtyp von `ErlaubterTyp` ist. Dies ist nützlich, wenn man die Typstabilität von Funktionen testet, die eine kleine Vereinigung wie `Union{Nothing, T}` oder `Union{Missing, T}` zurückgeben.

```jldoctest; setup = :(using InteractiveUtils; using Base: >), filter = r"begin\n(.|\n)*end"
julia> f(a) = a > 1 ? 1 : 1.0
f (generische Funktion mit 1 Methode)

julia> typeof(f(2))
Int64

julia> @code_warntype f(2)
MethodInstance für f(::Int64)
  von f(a) @ Main none:1
Argumente
  #self#::Core.Const(f)
  a::Int64
Body::UNION{FLOAT64, INT64}
1 ─ %1 = (a > 1)::Bool
└──      goto #3 if not %1
2 ─      return 1
3 ─      return 1.0

julia> @inferred f(2)
FEHLER: Rückgabetyp Int64 stimmt nicht mit abgeleitetem Rückgabetyp Union{Float64, Int64} überein
[...]

julia> @inferred max(1, 2)
2

julia> g(a) = a < 10 ? missing : 1.0
g (generische Funktion mit 1 Methode)

julia> @inferred g(20)
FEHLER: Rückgabetyp Float64 stimmt nicht mit abgeleitetem Rückgabetyp Union{Missing, Float64} überein
[...]

julia> @inferred Missing g(20)
1.0

julia> h(a) = a < 10 ? missing : f(a)
h (generische Funktion mit 1 Methode)

julia> @inferred Missing h(20)
FEHLER: Rückgabetyp Int64 stimmt nicht mit abgeleitetem Rückgabetyp Union{Missing, Float64, Int64} überein
[...]
```
