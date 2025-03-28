# Reflection and introspection

Julia offre une variété de capacités de réflexion à l'exécution.

## Module bindings

Les noms publics pour un `Module` sont disponibles en utilisant [`names(m::Module)`](@ref), ce qui renverra un tableau d'éléments [`Symbol`](@ref) représentant les liaisons publiques. `names(m::Module, all = true)` renvoie des symboles pour toutes les liaisons dans `m`, indépendamment du statut public.

## DataType fields

Les noms des champs `DataType` peuvent être interrogés en utilisant [`fieldnames`](@ref). Par exemple, étant donné le type suivant, `fieldnames(Point)` renvoie un tuple de [`Symbol`](@ref) représentant les noms des champs :

```jldoctest struct_point
julia> struct Point
           x::Int
           y
       end

julia> fieldnames(Point)
(:x, :y)
```

Le type de chaque champ dans un objet `Point` est stocké dans le champ `types` de la variable `Point` elle-même :

```jldoctest struct_point
julia> Point.types
svec(Int64, Any)
```

Alors que `x` est annoté comme un `Int`, `y` n'était pas annoté dans la définition de type, donc `y` par défaut au type `Any`.

Les types sont eux-mêmes représentés comme une structure appelée `DataType` :

```jldoctest struct_point
julia> typeof(Point)
DataType
```

Notez que `fieldnames(DataType)` donne les noms de chaque champ de `DataType` lui-même, et l'un de ces champs est le champ `types` observé dans l'exemple ci-dessus.

## Subtypes

Les *sous-types* *directs* de tout `DataType` peuvent être listés en utilisant [`subtypes`](@ref). Par exemple, le `DataType` abstrait [`AbstractFloat`](@ref) a quatre sous-types (concrets) :

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.subtypes(AbstractFloat)
5-element Vector{Any}:
 BigFloat
 Core.BFloat16
 Float16
 Float32
 Float64
```

Tout sous-type abstrait sera également inclus dans cette liste, mais d'autres sous-types en seront exclus ; l'application récursive de [`subtypes`](@ref) peut être utilisée pour inspecter l'arbre de types complet.

Notez que [`subtypes`](@ref) est situé à l'intérieur de [`InteractiveUtils`](@ref man-interactive-utils) mais est automatiquement exporté lors de l'utilisation du REPL.

## DataType layout

La représentation interne d'un `DataType` est d'une importance cruciale lors de l'interface avec le code C et plusieurs fonctions sont disponibles pour inspecter ces détails. [`isbitstype(T::DataType)`](@ref) renvoie vrai si `T` est stocké avec un alignement compatible C. [`fieldoffset(T::DataType, i::Integer)`](@ref) renvoie le décalage (en octets) pour le champ *i* par rapport au début du type.

## Function methods

Les méthodes de toute fonction générique peuvent être listées en utilisant [`methods`](@ref). La table de dispatch des méthodes peut être recherchée pour des méthodes acceptant un type donné en utilisant [`methodswith`](@ref).

## Expansion and lowering

Comme discuté dans la section [Metaprogramming](@ref), la fonction [`macroexpand`](@ref) donne l'expression non citée et interpolée ([`Expr`](@ref)) sous forme pour un macro donné. Pour utiliser `macroexpand`, `quote` le bloc d'expression lui-même (sinon, la macro sera évaluée et le résultat sera passé à la place !). Par exemple :

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.macroexpand(@__MODULE__, :(@edit println("")) )
:(InteractiveUtils.edit(println, (Base.typesof)("")))
```

Les fonctions `Base.Meta.show_sexpr` et [`dump`](@ref) sont utilisées pour afficher des vues au style S-expr et des vues de détails imbriquées en profondeur pour toute expression.

Enfin, la fonction [`Meta.lower`](@ref) donne la forme `lowered` de toute expression et est d'un intérêt particulier pour comprendre comment les constructions linguistiques se traduisent en opérations primitives telles que les affectations, les branches et les appels :

```jldoctest; setup = (using Base: +, sin)
julia> Meta.lower(@__MODULE__, :( [1+2, sin(0.5)] ))
:($(Expr(:thunk, CodeInfo(
    @ none within `top-level scope`
1 ─ %1 = 1 + 2
│   %2 = sin(0.5)
│   %3 = Base.vect(%1, %2)
└──      return %3
))))
```

## Intermediate and compiled representations

Inspecter la forme abaissée des fonctions nécessite de sélectionner la méthode spécifique à afficher, car les fonctions génériques peuvent avoir de nombreuses méthodes avec des signatures de type différentes. À cette fin, un code d'abaissement spécifique à la méthode est disponible en utilisant [`code_lowered`](@ref), et la forme inférée par le type est disponible en utilisant [`code_typed`](@ref). [`code_warntype`](@ref) ajoute une mise en surbrillance à la sortie de `4d61726b646f776e2e436f64652822222c2022636f64655f74797065642229_40726566`.

Plus près de la machine, la représentation intermédiaire LLVM d'une fonction peut être imprimée en utilisant [`code_llvm`](@ref), et enfin le code machine compilé est disponible en utilisant [`code_native`](@ref) (cela déclenchera la compilation JIT/génération de code pour toute fonction qui n'a pas été appelée précédemment).

Pour plus de commodité, il existe des versions macro des fonctions ci-dessus qui prennent des appels de fonction standard et étendent automatiquement les types d'arguments :

```julia-repl
julia> @code_llvm +(1,1)
;  @ int.jl:87 within `+`
; Function Attrs: sspstrong uwtable
define i64 @"julia_+_476"(i64 signext %0, i64 signext %1) #0 {
top:
  %2 = add i64 %1, %0
  ret i64 %2
}
```

Pour plus d'informations, voir [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_warntype`](@ref), [`@code_llvm`](@ref), et [`@code_native`](@ref).

### Printing of debug information

Les fonctions et macros mentionnées ci-dessus prennent l'argument clé `debuginfo` qui contrôle le niveau des informations de débogage imprimées.

```jldoctest; setup = :(using InteractiveUtils), filter = r"int.jl:\d+"
julia> InteractiveUtils.@code_typed debuginfo=:source +(1,1)
CodeInfo(
    @ int.jl:87 within `+`
1 ─ %1 = Base.add_int(x, y)::Int64
└──      return %1
) => Int64
```

Les valeurs possibles pour `debuginfo` sont : `:none`, `:source` et `:default`. Par défaut, les informations de débogage ne sont pas imprimées, mais cela peut être modifié en définissant `Base.IRShow.default_debuginfo[] = :source`.
