```
Ref{T}
```

Un objet qui référence en toute sécurité des données de type `T`. Ce type est garanti de pointer vers une mémoire valide, allouée par Julia, du type correct. Les données sous-jacentes sont protégées de la libération par le ramasse-miettes tant que le `Ref` lui-même est référencé.

En Julia, les objets `Ref` sont déréférencés (chargés ou stockés) avec `[]`.

La création d'un `Ref` pour une valeur `x` de type `T` s'écrit généralement `Ref(x)`. De plus, pour créer des pointeurs intérieurs vers des conteneurs (comme Array ou Ptr), cela peut s'écrire `Ref(a, i)` pour créer une référence à l'élément `i`-ème de `a`.

`Ref{T}()` crée une référence à une valeur de type `T` sans initialisation. Pour un type de bits `T`, la valeur sera ce qui réside actuellement dans la mémoire allouée. Pour un type non-bit `T`, la référence sera indéfinie et tenter de la déréférencer entraînera une erreur, "UndefRefError: accès à une référence indéfinie".

Pour vérifier si un `Ref` est une référence indéfinie, utilisez [`isassigned(ref::RefValue)`](@ref). Par exemple, `isassigned(Ref{T}())` est `false` si `T` n'est pas un type de bits. Si `T` est un type de bits, `isassigned(Ref{T}())` sera toujours vrai.

Lorsqu'il est passé comme argument `ccall` (soit en tant que type `Ptr` ou `Ref`), un objet `Ref` sera converti en un pointeur natif vers les données qu'il référence. Pour la plupart des `T`, ou lorsqu'il est converti en `Ptr{Cvoid}`, il s'agit d'un pointeur vers les données de l'objet. Lorsque `T` est un type `isbits`, cette valeur peut être mutée en toute sécurité, sinon la mutation est strictement un comportement indéfini.

Dans un cas particulier, définir `T = Any` entraînera plutôt la création d'un pointeur vers la référence elle-même lorsqu'il est converti en `Ptr{Any}` (un `jl_value_t const* const*` si T est immuable, sinon un `jl_value_t *const *`). Lorsqu'il est converti en `Ptr{Cvoid}`, il renverra toujours un pointeur vers la région de données comme pour tout autre `T`.

Une instance `C_NULL` de `Ptr` peut être passée à un argument `ccall` `Ref` pour l'initialiser.

# Utilisation dans le broadcasting

`Ref` est parfois utilisé dans le broadcasting afin de traiter les valeurs référencées comme un scalaire.

# Exemples

```jldoctest
julia> r = Ref(5) # Créer un Ref avec une valeur initiale
Base.RefValue{Int64}(5)

julia> r[] # Obtenir une valeur d'un Ref
5

julia> r[] = 7 # Stocker une nouvelle valeur dans un Ref
7

julia> r # Le Ref contient maintenant 7
Base.RefValue{Int64}(7)

julia> isa.(Ref([1,2,3]), [Array, Dict, Int]) # Traiter les valeurs de référence comme des scalaires lors du broadcasting
BitVector de 3 éléments :
 1
 0
 0

julia> Ref{Function}()  # Référence indéfinie à un type non-bit, Function
Base.RefValue{Function}(#undef)

julia> try
           Ref{Function}()[] # Déréférencer une référence indéfinie entraînera une erreur
       catch e
           println(e)
       end
UndefRefError()

julia> Ref{Int64}()[]; # Une référence à un type de bits fait référence à une valeur indéterminée si non donnée

julia> isassigned(Ref{Int64}()) # Une référence à un type de bits est toujours assignée
true
```
