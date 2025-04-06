```
=
```

`=` est l'opérateur d'assignation.

  * Pour la variable `a` et l'expression `b`, `a = b` fait que `a` fait référence à la valeur de `b`.
  * Pour les fonctions `f(x)`, `f(x) = x` définit une nouvelle constante de fonction `f`, ou ajoute une nouvelle méthode à `f` si `f` est déjà défini ; cette utilisation est équivalente à `function f(x); x; end`.
  * `a[i] = v` appelle [`setindex!`](@ref)`(a,v,i)`.
  * `a.b = c` appelle [`setproperty!`](@ref)`(a,:b,c)`.
  * À l'intérieur d'un appel de fonction, `f(a=b)` passe `b` comme la valeur de l'argument clé `a`.
  * À l'intérieur de parenthèses avec des virgules, `(a=1,)` construit un [`NamedTuple`](@ref).

# Exemples

L'assignation de `a` à `b` ne crée pas une copie de `b` ; utilisez plutôt [`copy`](@ref) ou [`deepcopy`](@ref).

```jldoctest
julia> b = [1]; a = b; b[1] = 2; a
1-element Array{Int64, 1}:
 2

julia> b = [1]; a = copy(b); b[1] = 2; a
1-element Array{Int64, 1}:
 1

```

Les collections passées aux fonctions ne sont également pas copiées. Les fonctions peuvent modifier (muter) le contenu des objets auxquels leurs arguments font référence. (Les noms des fonctions qui font cela sont conventionnellement suffixés par '!'.)

```jldoctest
julia> function f!(x); x[:] .+= 1; end
f! (generic function with 1 method)

julia> a = [1]; f!(a); a
1-element Array{Int64, 1}:
 2

```

L'assignation peut fonctionner sur plusieurs variables en parallèle, prenant des valeurs d'un itérable :

```jldoctest
julia> a, b = 4, 5
(4, 5)

julia> a, b = 1:3
1:3

julia> a, b
(1, 2)

```

L'assignation peut fonctionner sur plusieurs variables en série, et renverra la valeur de l'expression la plus à droite :

```jldoctest
julia> a = [1]; b = [2]; c = [3]; a = b = c
1-element Array{Int64, 1}:
 3

julia> b[1] = 2; a, b, c
([2], [2], [2])

```

L'assignation à des indices hors limites ne fait pas croître une collection. Si la collection est un [`Vector`](@ref), elle peut plutôt être agrandie avec [`push!`](@ref) ou [`append!`](@ref).

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

L'assignation de `[]` n'élimine pas les éléments d'une collection ; utilisez plutôt [`filter!`](@ref).

```jldoctest
julia> a = collect(1:3); a[a .<= 1] = []
ERROR: DimensionMismatch: tried to assign 0 elements to 1 destinations
[...]

julia> filter!(x -> x > 1, a) # in-place & thus more efficient than a = a[a .> 1]
2-element Array{Int64, 1}:
 2
 3

```
