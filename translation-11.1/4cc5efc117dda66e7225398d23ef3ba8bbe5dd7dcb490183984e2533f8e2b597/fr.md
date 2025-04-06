# More about types

Si vous avez utilisé Julia pendant un certain temps, vous comprenez le rôle fondamental que jouent les types. Ici, nous essayons de nous plonger dans les détails, en nous concentrant particulièrement sur [Parametric Types](@ref).

## Types and sets (and `Any` and `Union{}`/`Bottom`)

Il est peut-être plus facile de concevoir le système de types de Julia en termes d'ensembles. Alors que les programmes manipulent des valeurs individuelles, un type fait référence à un ensemble de valeurs. Ce n'est pas la même chose qu'une collection ; par exemple, un [`Set`](@ref) de valeurs est lui-même une seule valeur `Set`. Au contraire, un type décrit un ensemble de valeurs *possibles*, exprimant une incertitude quant à la valeur que nous avons.

Un type *concret* `T` décrit l'ensemble des valeurs dont l'étiquette directe, telle que retournée par la fonction [`typeof`](@ref), est `T`. Un type *abstrait* décrit un ensemble de valeurs potentiellement plus grand.

[`Any`](@ref) décrit l'ensemble de l'univers des valeurs possibles. [`Integer`](@ref) est un sous-ensemble de `Any` qui inclut `Int`, [`Int8`](@ref), et d'autres types concrets. En interne, Julia utilise également un autre type connu sous le nom de `Bottom`, qui peut également être écrit comme `Union{}`. Cela correspond à l'ensemble vide.

Les types de Julia prennent en charge les opérations standard de la théorie des ensembles : vous pouvez demander si `T1` est un "sous-ensemble" (sous-type) de `T2` avec `T1 <: T2`. De même, vous pouvez intersecter deux types en utilisant [`typeintersect`](@ref), prendre leur union avec [`Union`](@ref), et calculer un type qui contient leur union avec [`typejoin`](@ref) :

```jldoctest
julia> typeintersect(Int, Float64)
Union{}

julia> Union{Int, Float64}
Union{Float64, Int64}

julia> typejoin(Int, Float64)
Real

julia> typeintersect(Signed, Union{UInt8, Int8})
Int8

julia> Union{Signed, Union{UInt8, Int8}}
Union{UInt8, Signed}

julia> typejoin(Signed, Union{UInt8, Int8})
Integer

julia> typeintersect(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Int64, Float64}

julia> Union{Tuple{Integer, Float64}, Tuple{Int, Real}}
Union{Tuple{Int64, Real}, Tuple{Integer, Float64}}

julia> typejoin(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Integer, Real}
```

Bien que ces opérations puissent sembler abstraites, elles sont au cœur de Julia. Par exemple, la dispatch de méthode est implémentée en parcourant les éléments d'une liste de méthodes jusqu'à atteindre celle pour laquelle le type du tuple d'arguments est un sous-type de la signature de la méthode. Pour que cet algorithme fonctionne, il est important que les méthodes soient triées par leur spécificité, et que la recherche commence par les méthodes les plus spécifiques. Par conséquent, Julia implémente également un ordre partiel sur les types ; cela est réalisé par une fonctionnalité similaire à `<:`, mais avec des différences qui seront discutées ci-dessous.

## UnionAll types

Le système de types de Julia peut également exprimer une *union itérée* de types : une union de types sur toutes les valeurs d'une certaine variable. Cela est nécessaire pour décrire des types paramétriques où les valeurs de certains paramètres ne sont pas connues.

Par exemple, [`Array`](@ref) a deux paramètres comme dans `Array{Int,2}`. Si nous ne connaissions pas le type d'élément, nous pourrions écrire `Array{T,2} where T`, qui est l'union de `Array{T,2}` pour toutes les valeurs de `T` : `Union{Array{Int8,2}, Array{Int16,2}, ...}`.

Un tel type est représenté par un objet `UnionAll`, qui contient une variable (`T` dans cet exemple, de type `TypeVar`), et un type enveloppé (`Array{T,2}` dans cet exemple).

Considérez les méthodes suivantes :

```julia
f1(A::Array) = 1
f2(A::Array{Int}) = 2
f3(A::Array{T}) where {T<:Any} = 3
f4(A::Array{Any}) = 4
```

La signature - comme décrite dans [Function calls](@ref Function-calls) - de `f3` est un type `UnionAll` englobant un type tuple : `Tuple{typeof(f3), Array{T}} où T`. Tous sauf `f4` peuvent être appelés avec `a = [1,2]` ; tous sauf `f2` peuvent être appelés avec `b = Any[1,2]`.

Examinons ces types de plus près :

```jldoctest
julia> dump(Array)
UnionAll
  var: TypeVar
    name: Symbol T
    lb: Union{}
    ub: Any
  body: UnionAll
    var: TypeVar
      name: Symbol N
      lb: Union{}
      ub: Any
    body: Array{T, N} <: DenseArray{T, N}
      ref::MemoryRef{T}
      size::NTuple{N, Int64}
```

Cela indique que `Array` nomme en réalité un type `UnionAll`. Il existe un type `UnionAll` pour chaque paramètre, imbriqué. La syntaxe `Array{Int,2}` est équivalente à `Array{Int}{2}` ; en interne, chaque `UnionAll` est instancié avec une valeur de variable particulière, un à la fois, en commençant par l'extérieur. Cela donne un sens naturel à l'omission des paramètres de type finaux ; `Array{Int}` donne un type équivalent à `Array{Int,N} où N`.

Un `TypeVar` n'est pas en soi un type, mais doit plutôt être considéré comme faisant partie de la structure d'un type `UnionAll`. Les variables de type ont des bornes inférieure et supérieure sur leurs valeurs (dans les champs `lb` et `ub`). Le symbole `name` est purement cosmétique. En interne, les `TypeVar` sont comparés par adresse, ils sont donc définis comme des types mutables pour garantir que des variables de type "différentes" peuvent être distinguées. Cependant, par convention, elles ne devraient pas être mutées.

On peut construire des `TypeVar`s manuellement :

```jldoctest
julia> TypeVar(:V, Signed, Real)
Signed<:V<:Real
```

Il existe des versions pratiques qui vous permettent d'omettre l'un de ces arguments, sauf le symbole `name`.

La syntaxe `Array{T} where T<:Integer` est abaissée à

```julia
let T = TypeVar(:T,Integer)
    UnionAll(T, Array{T})
end
```

il est donc rarement nécessaire de construire un `TypeVar` manuellement (en effet, cela doit être évité).

## Free variables

Le concept d'une variable de type *libre* est extrêmement important dans le système de types. Nous disons qu'une variable `V` est libre dans le type `T` si `T` ne contient pas le `UnionAll` qui introduit la variable `V`. Par exemple, le type `Array{Array{V} where V<:Integer}` n'a pas de variables libres, mais la partie `Array{V}` à l'intérieur en a une variable libre, `V`.

Un type avec des variables libres n'est, en quelque sorte, pas vraiment un type du tout. Considérons le type `Array{Array{T}} where T`, qui fait référence à tous les tableaux homogènes de tableaux. Le type interne `Array{T}`, vu par lui-même, pourrait sembler faire référence à n'importe quel type de tableau. Cependant, chaque élément du tableau externe doit avoir le *même* type de tableau, donc `Array{T}` ne peut pas faire référence à n'importe quel ancien tableau. On pourrait dire que `Array{T}` "apparaît" effectivement plusieurs fois, et que `T` doit avoir la même valeur à chaque "fois".

Pour cette raison, la fonction `jl_has_free_typevars` dans l'API C est très importante. Les types pour lesquels elle retourne vrai ne donneront pas de réponses significatives dans le sous-typage et d'autres fonctions de type.

## TypeNames

Les deux types suivants [`Array`](@ref) sont fonctionnellement équivalents, mais s'impriment différemment :

```jldoctest
julia> TV, NV = TypeVar(:T), TypeVar(:N)
(T, N)

julia> Array
Array

julia> Array{TV, NV}
Array{T, N}
```

Cela peut être distingué en examinant le champ `name` du type, qui est un objet de type `TypeName` :

```julia-repl
julia> dump(Array{Int,1}.name)
TypeName
  name: Symbol Array
  module: Module Core
  names: empty SimpleVector
  wrapper: UnionAll
    var: TypeVar
      name: Symbol T
      lb: Union{}
      ub: Any
    body: UnionAll
      var: TypeVar
        name: Symbol N
        lb: Union{}
        ub: Any
      body: Array{T, N} <: DenseArray{T, N}
  cache: SimpleVector
    ...

  linearcache: SimpleVector
    ...

  hash: Int64 -7900426068641098781
  mt: MethodTable
    name: Symbol Array
    defs: Nothing nothing
    cache: Nothing nothing
    max_args: Int64 0
    module: Module Core
    : Int64 0
    : Int64 0
```

Dans ce cas, le champ pertinent est `wrapper`, qui contient une référence au type de niveau supérieur utilisé pour créer de nouveaux types `Array`.

```julia-repl
julia> pointer_from_objref(Array)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array.body.body.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array{TV,NV})
Ptr{Cvoid} @0x00007fcc80c4d930

julia> pointer_from_objref(Array{TV,NV}.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850
```

Le champ `wrapper` de [`Array`](@ref) pointe vers lui-même, mais pour `Array{TV,NV}`, il renvoie à la définition originale du type.

Que dire des autres champs ? `hash` attribue un entier à chaque type. Pour examiner le champ `cache`, il est utile de choisir un type qui est moins utilisé que Array. Créons d'abord notre propre type :

```jldoctest
julia> struct MyType{T,N} end

julia> MyType{Int,2}
MyType{Int64, 2}

julia> MyType{Float32, 5}
MyType{Float32, 5}
```

Lorsque vous instanciez un type paramétrique, chaque type concret est enregistré dans un cache de type (`MyType.body.body.name.cache`). Cependant, les instances contenant des variables de type libres ne sont pas mises en cache.

## Tuple types

Les types de tuples constituent un cas spécial intéressant. Pour que le dispatch fonctionne sur des déclarations comme `x::Tuple`, le type doit être capable d'accommoder n'importe quel tuple. Vérifions les paramètres :

```jldoctest
julia> Tuple
Tuple

julia> Tuple.parameters
svec(Vararg{Any})
```

Contrairement à d'autres types, les types de tuples sont covariants dans leurs paramètres, donc cette définition permet à `Tuple` de correspondre à n'importe quel type de tuple :

```jldoctest
julia> typeintersect(Tuple, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{Any}}, Tuple{Int,Float64})
Tuple{Int64, Float64}
```

Cependant, si un type de tuple variadique (`Vararg`) a des variables libres, il peut décrire différents types de tuples :

```jldoctest
julia> typeintersect(Tuple{Vararg{T} where T}, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{T}} where T, Tuple{Int,Float64})
Union{}
```

Remarquez que lorsque `T` est libre par rapport au type `Tuple` (c'est-à-dire que son type de liaison `UnionAll` est en dehors du type `Tuple`), une seule valeur `T` doit fonctionner sur l'ensemble du type. Par conséquent, un tuple hétérogène ne correspond pas.

Enfin, il convient de noter que `Tuple{}` est distinct :

```jldoctest
julia> Tuple{}
Tuple{}

julia> Tuple{}.parameters
svec()

julia> typeintersect(Tuple{}, Tuple{Int})
Union{}
```

Quel est le type de tuple "primaire" ?

```julia-repl
julia> pointer_from_objref(Tuple)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{})
Ptr{Cvoid} @0x00007f5998a570d0

julia> pointer_from_objref(Tuple.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{}.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370
```

donc `Tuple == Tuple{Vararg{Any}}` est en effet le type principal.

## Diagonal types

Considérez le type `Tuple{T,T} where T`. Une méthode avec cette signature ressemblerait à :

```julia
f(x::T, y::T) where {T} = ...
```

Selon l'interprétation habituelle d'un type `UnionAll`, ce `T` couvre tous les types, y compris `Any`, donc ce type devrait être équivalent à `Tuple{Any,Any}`. Cependant, cette interprétation pose certains problèmes pratiques.

Tout d'abord, une valeur de `T` doit être disponible à l'intérieur de la définition de la méthode. Pour un appel comme `f(1, 1.0)`, il n'est pas clair ce que `T` devrait être. Cela pourrait être `Union{Int,Float64}`, ou peut-être [`Real`](@ref). Intuitivement, nous nous attendons à ce que la déclaration `x::T` signifie `T === typeof(x)`. Pour s'assurer que cette invariant est respecté, nous avons besoin que `typeof(x) === typeof(y) === T` dans cette méthode. Cela implique que la méthode ne doit être appelée que pour des arguments du même type exact.

Il s'avère qu'être capable de dispatcher sur le fait que deux valeurs ont le même type est très utile (cela est utilisé par le système de promotion par exemple), donc nous avons plusieurs raisons de vouloir une interprétation différente de `Tuple{T,T} where T`. Pour faire fonctionner cela, nous ajoutons la règle suivante à la sous-typage : si une variable apparaît plus d'une fois en position covariante, elle est restreinte à ne varier que sur des types concrets. ("Position covariante" signifie que seuls les types `Tuple` et `Union` apparaissent entre une occurrence d'une variable et le type `UnionAll` qui l'introduit.) De telles variables sont appelées "variables diagonales" ou "variables concrètes".

Ainsi, par exemple, `Tuple{T,T} where T` peut être vu comme `Union{Tuple{Int8,Int8}, Tuple{Int16,Int16}, ...}`, où `T` varie sur tous les types concrets. Cela donne lieu à des résultats de sous-typage intéressants. Par exemple, `Tuple{Real,Real}` n'est pas un sous-type de `Tuple{T,T} where T`, car il inclut certains types comme `Tuple{Int8,Int16}` où les deux éléments ont des types différents. `Tuple{Real,Real}` et `Tuple{T,T} where T` ont l'intersection non triviale `Tuple{T,T} where T<:Real`. Cependant, `Tuple{Real}` *est* un sous-type de `Tuple{T} where T`, car dans ce cas, `T` apparaît seulement une fois et n'est donc pas diagonal.

Ensuite, considérez une signature comme celle-ci :

```julia
f(a::Array{T}, x::T, y::T) where {T} = ...
```

Dans ce cas, `T` se trouve en position invariante à l'intérieur de `Array{T}`. Cela signifie que quel que soit le type de tableau passé, cela détermine sans ambiguïté la valeur de `T` – nous disons que `T` a une *contrainte d'égalité* sur lui. Par conséquent, dans ce cas, la règle diagonale n'est pas vraiment nécessaire, puisque le tableau détermine `T` et nous pouvons alors permettre à `x` et `y` d'être de n'importe quel sous-type de `T`. Ainsi, les variables qui se trouvent en position invariante ne sont jamais considérées comme diagonales. Ce choix de comportement est légèrement controversé – certains estiment que cette définition devrait être écrite comme

```julia
f(a::Array{T}, x::S, y::S) where {T, S<:T} = ...
```

pour clarifier si `x` et `y` doivent avoir le même type. Dans cette version de la signature, ils le feraient, ou nous pourrions introduire une troisième variable pour le type de `y` si `x` et `y` peuvent avoir des types différents.

La prochaine complication est l'interaction des unions et des variables diagonales, par exemple.

```julia
f(x::Union{Nothing,T}, y::T) where {T} = ...
```

Considérez ce que signifie cette déclaration. `y` a le type `T`. `x` peut alors avoir soit le même type `T`, soit être de type [`Nothing`](@ref). Ainsi, tous les appels suivants devraient correspondre :

```julia
f(1, 1)
f("", "")
f(2.0, 2.0)
f(nothing, 1)
f(nothing, "")
f(nothing, 2.0)
```

Ces exemples nous disent quelque chose : lorsque `x` est `nothing::Nothing`, il n'y a pas de contraintes supplémentaires sur `y`. C'est comme si la signature de la méthode avait `y::Any`. En effet, nous avons l'équivalence de type suivante :

```julia
(Tuple{Union{Nothing,T},T} where T) == Union{Tuple{Nothing,Any}, Tuple{T,T} where T}
```

La règle générale est la suivante : une variable concrète en position covariante agit comme si elle n'était pas concrète si l'algorithme de sous-typage ne l'*utilise* qu'une seule fois. Lorsque `x` a le type `Nothing`, nous n'avons pas besoin d'utiliser le `T` dans `Union{Nothing,T}` ; nous ne l'utilisons que dans la deuxième position. Cela découle naturellement de l'observation que dans `Tuple{T} where T`, restreindre `T` à des types concrets ne fait aucune différence ; le type est égal à `Tuple{Any}` dans les deux cas.

Cependant, apparaître en position *invariante* disqualifie une variable d'être concrète, que cette apparition de la variable soit utilisée ou non. Sinon, les types peuvent se comporter différemment selon les autres types auxquels ils sont comparés, rendant le sous-typage non transitif. Par exemple, considérons

```julia
Tuple{Int,Int8,Vector{Integer}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Si le `T` à l'intérieur de l'`Union` est ignoré, alors `T` est concret et la réponse est "faux" puisque les deux premiers types ne sont pas les mêmes. Mais considérons plutôt

```julia
Tuple{Int,Int8,Vector{Any}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Maintenant, nous ne pouvons pas ignorer le `T` dans le `Union` (nous devons avoir `T == Any`), donc `T` n'est pas concret et la réponse est "vrai". Cela ferait dépendre la concrétude de `T` du autre type, ce qui n'est pas acceptable puisque un type doit avoir une signification claire par lui-même. Par conséquent, l'apparition de `T` à l'intérieur de `Vector` est considérée dans les deux cas.

## Subtyping diagonal variables

L'algorithme de sous-typage pour les variables diagonales a deux composants : (1) identifier les occurrences de variables, et (2) s'assurer que les variables diagonales ne varient que sur des types concrets.

La première tâche est accomplie en maintenant des compteurs `occurs_inv` et `occurs_cov` (dans `src/subtype.c`) pour chaque variable dans l'environnement, suivant le nombre d'occurrences invariantes et covariantes, respectivement. Une variable est diagonale lorsque `occurs_inv == 0 && occurs_cov > 1`.

La deuxième tâche est accomplie en imposant une condition sur la borne inférieure d'une variable. Au fur et à mesure que l'algorithme de sous-typage s'exécute, il affine les bornes de chaque variable (élevant les bornes inférieures et abaissant les bornes supérieures) pour suivre la plage des valeurs de variable pour lesquelles la relation de sous-type serait valable. Lorsque nous avons terminé d'évaluer le corps d'un type `UnionAll` dont la variable est diagonale, nous examinons les valeurs finales des bornes. Étant donné que la variable doit être concrète, une contradiction se produit si sa borne inférieure ne peut pas être un sous-type d'un type concret. Par exemple, un type abstrait comme [`AbstractArray`](@ref) ne peut pas être un sous-type d'un type concret, mais un type concret comme `Int` peut l'être, et le type vide `Bottom` peut également l'être. Si une borne inférieure échoue à ce test, l'algorithme s'arrête avec la réponse `false`.

Par exemple, dans le problème `Tuple{Int,String} <: Tuple{T,T} where T`, nous déduisons que cela serait vrai si `T` était un supertype de `Union{Int,String}`. Cependant, `Union{Int,String}` est un type abstrait, donc la relation ne tient pas.

Ce test de concrétude est effectué par la fonction `is_leaf_bound`. Notez que ce test est légèrement différent de `jl_is_leaf_type`, car il renvoie également `true` pour `Bottom`. Actuellement, cette fonction est heuristique et ne capture pas tous les types concrets possibles. La difficulté réside dans le fait que la concrétude d'une borne inférieure peut dépendre des valeurs des autres bornes de variables de type. Par exemple, `Vector{T}` est équivalent au type concret `Vector{Int}` uniquement si les bornes supérieures et inférieures de `T` sont toutes deux égales à `Int`. Nous n'avons pas encore élaboré d'algorithme complet pour cela.

## Introduction to the internal machinery

La plupart des opérations liées aux types se trouvent dans les fichiers `jltypes.c` et `subtype.c`. Une bonne façon de commencer est d'observer le sous-typage en action. Construisez Julia avec `make debug` et lancez Julia dans un débogueur. [gdb debugging tips](@ref gdb-debugging-tips) contient quelques conseils qui peuvent être utiles.

Parce que le code de sous-typage est utilisé intensivement dans le REPL lui-même – et donc les points d'arrêt dans ce code sont souvent déclenchés – il sera plus facile si vous faites la définition suivante :

```julia-repl
julia> function mysubtype(a,b)
           ccall(:jl_breakpoint, Cvoid, (Any,), nothing)
           a <: b
       end
```

et ensuite définissez un point d'arrêt dans `jl_breakpoint`. Une fois que ce point d'arrêt est déclenché, vous pouvez définir des points d'arrêt dans d'autres fonctions.

En guise d'échauffement, essayez ce qui suit :

```julia
mysubtype(Tuple{Int, Float64}, Tuple{Integer, Real})
```

Nous pouvons le rendre plus intéressant en essayant un cas plus complexe :

```julia
mysubtype(Tuple{Array{Int,2}, Int8}, Tuple{Array{T}, T} where T)
```

## Subtyping and method sorting

Les fonctions `type_morespecific` sont utilisées pour imposer un ordre partiel sur les fonctions dans les tables de méthodes (du plus spécifique au moins spécifique). La spécificité est stricte ; si `a` est plus spécifique que `b`, alors `a` n'est pas égal à `b` et `b` n'est pas plus spécifique que `a`.

Si `a` est un sous-type strict de `b`, alors il est automatiquement considéré comme plus spécifique. À partir de là, `type_morespecific` utilise certaines règles moins formelles. Par exemple, `subtype` est sensible au nombre d'arguments, mais `type_morespecific` peut ne pas l'être. En particulier, `Tuple{Int,AbstractFloat}` est plus spécifique que `Tuple{Integer}`, même s'il n'est pas un sous-type. (Entre `Tuple{Int,AbstractFloat}` et `Tuple{Integer,Float64}`, aucun n'est plus spécifique que l'autre.) De même, `Tuple{Int,Vararg{Int}}` n'est pas un sous-type de `Tuple{Integer}`, mais il est considéré comme plus spécifique. Cependant, `morespecific` obtient un bonus pour la longueur : en particulier, `Tuple{Int,Int}` est plus spécifique que `Tuple{Int,Vararg{Int}}`.

Si vous déboguez comment les méthodes sont triées, il peut être pratique de définir la fonction :

```julia
type_morespecific(a, b) = ccall(:jl_type_morespecific, Cint, (Any,Any), a, b)
```

qui vous permet de tester si le type de tuple `a` est plus spécifique que le type de tuple `b`.
