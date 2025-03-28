```
=
```

`=` es el operador de asignación.

  * Para la variable `a` y la expresión `b`, `a = b` hace que `a` se refiera al valor de `b`.
  * Para funciones `f(x)`, `f(x) = x` define una nueva constante de función `f`, o agrega un nuevo método a `f` si `f` ya está definido; este uso es equivalente a `function f(x); x; end`.
  * `a[i] = v` llama a [`setindex!`](@ref)`(a,v,i)`.
  * `a.b = c` llama a [`setproperty!`](@ref)`(a,:b,c)`.
  * Dentro de una llamada a función, `f(a=b)` pasa `b` como el valor del argumento de palabra clave `a`.
  * Dentro de paréntesis con comas, `(a=1,)` construye un [`NamedTuple`](@ref).

# Ejemplos

Asignar `a` a `b` no crea una copia de `b`; en su lugar, usa [`copy`](@ref) o [`deepcopy`](@ref).

```jldoctest
julia> b = [1]; a = b; b[1] = 2; a
1-element Array{Int64, 1}:
 2

julia> b = [1]; a = copy(b); b[1] = 2; a
1-element Array{Int64, 1}:
 1

```

Las colecciones pasadas a funciones tampoco se copian. Las funciones pueden modificar (mutar) el contenido de los objetos a los que se refieren sus argumentos. (Los nombres de las funciones que hacen esto se les añade convencionalmente un sufijo '!'.)

```jldoctest
julia> function f!(x); x[:] .+= 1; end
f! (generic function with 1 method)

julia> a = [1]; f!(a); a
1-element Array{Int64, 1}:
 2

```

La asignación puede operar en múltiples variables en paralelo, tomando valores de un iterable:

```jldoctest
julia> a, b = 4, 5
(4, 5)

julia> a, b = 1:3
1:3

julia> a, b
(1, 2)

```

La asignación puede operar en múltiples variables en serie, y devolverá el valor de la expresión más a la derecha:

```jldoctest
julia> a = [1]; b = [2]; c = [3]; a = b = c
1-element Array{Int64, 1}:
 3

julia> b[1] = 2; a, b, c
([2], [2], [2])

```

La asignación en índices fuera de límites no hace crecer una colección. Si la colección es un [`Vector`](@ref) se puede hacer crecer en su lugar con [`push!`](@ref) o [`append!`](@ref).

```jldoctest
julia> a = [1, 1]; a[3] = 2
ERROR: BoundsError: attempt to access 2-element Array{Int64, 1} at index [3]
[...]

julia> push!(a, 2, 3)
4-element Array{Int64, 1}:
 1
 1
 2
 3

```

Asignar `[]` no elimina elementos de una colección; en su lugar, usa [`filter!`](@ref).

```jldoctest
julia> a = collect(1:3); a[a .<= 1] = []
ERROR: DimensionMismatch: tried to assign 0 elements to 1 destinations
[...]

julia> filter!(x -> x > 1, a) # in-place & thus more efficient than a = a[a .> 1]
2-element Array{Int64, 1}:
 2
 3

```
