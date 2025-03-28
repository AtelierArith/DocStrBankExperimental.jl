```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Random/docs/src/index.md"
```

# Random Numbers

```@meta
DocTestSetup = :(using Random)
```

La génération de nombres aléatoires en Julia utilise par défaut l'algorithme [Xoshiro256++](https://prng.di.unimi.it/), avec un état par `Task`. D'autres types de générateurs de nombres aléatoires peuvent être intégrés en héritant du type `AbstractRNG` ; ils peuvent ensuite être utilisés pour obtenir plusieurs flux de nombres aléatoires.

Les PRNG (générateurs de nombres pseudo-aléatoires) exportés par le paquet `Random` sont :

  * `TaskLocalRNG` : un jeton qui représente l'utilisation du flux local à la tâche actuellement actif, semé de manière déterministe à partir de la tâche parente, ou par `RandomDevice` (avec de l'aléa système) au démarrage du programme.
  * `Xoshiro` : génère un flux de nombres aléatoires de haute qualité avec un petit vecteur d'état et des performances élevées en utilisant l'algorithme Xoshiro256++
  * `RandomDevice`: pour l'entropie fournie par le système d'exploitation. Cela peut être utilisé pour des nombres aléatoires cryptographiquement sécurisés (CS(P)RNG).
  * `MersenneTwister` : un PRNG de haute qualité alternatif qui était le défaut dans les anciennes versions de Julia, et qui est également assez rapide, mais nécessite beaucoup plus d'espace pour stocker le vecteur d'état et générer une séquence aléatoire.

La plupart des fonctions liées à la génération aléatoire acceptent un objet `AbstractRNG` optionnel comme premier argument. Certaines acceptent également des spécifications de dimensions `dims...` (qui peuvent également être données sous forme de tuple) pour générer des tableaux de valeurs aléatoires. Dans un programme multi-thread, vous devriez généralement utiliser différents objets RNG provenant de différents threads ou tâches afin d'être thread-safe. Cependant, le RNG par défaut est thread-safe depuis Julia 1.3 (utilisant un RNG par thread jusqu'à la version 1.6, et par tâche par la suite).

Les RNG fournis peuvent générer des nombres aléatoires uniformes des types suivants : [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref), [`BigFloat`](@ref), [`Bool`](@ref), [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`BigInt`](@ref) (ou des nombres complexes de ces types). Des nombres flottants aléatoires sont générés uniformément dans $[0, 1)$. Comme `BigInt` représente des entiers non bornés, l'intervalle doit être spécifié (par exemple, `rand(big.(1:6))`).

De plus, des distributions normales et exponentielles sont implémentées pour certains types `AbstractFloat` et `Complex`, voir [`randn`](@ref) et [`randexp`](@ref) pour plus de détails.

Pour générer des nombres aléatoires à partir d'autres distributions, consultez le package [Distributions.jl](https://juliastats.org/Distributions.jl/stable/).

!!! warning
    Parce que la manière précise dont les nombres aléatoires sont générés est considérée comme un détail d'implémentation, les corrections de bogues et les améliorations de vitesse peuvent modifier le flux de nombres générés après un changement de version. Il est donc déconseillé de s'appuyer sur une graine spécifique ou un flux de nombres générés lors des tests unitaires - envisagez plutôt de tester les propriétés des méthodes en question.


## Random numbers module

```@docs
Random.Random
```

## Random generation functions

```@docs
Random.rand
Random.rand!
Random.bitrand
Random.randn
Random.randn!
Random.randexp
Random.randexp!
Random.randstring
```

## Subsequences, permutations and shuffling

```@docs
Random.randsubseq
Random.randsubseq!
Random.randperm
Random.randperm!
Random.randcycle
Random.randcycle!
Random.shuffle
Random.shuffle!
```

## Generators (creation and seeding)

```@docs
Random.default_rng
Random.seed!
Random.AbstractRNG
Random.TaskLocalRNG
Random.Xoshiro
Random.MersenneTwister
Random.RandomDevice
```

## [Hooking into the `Random` API](@id rand-api-hook)

Il existe deux manières principalement orthogonales d'étendre les fonctionnalités de `Random` :

1. génération de valeurs aléatoires de types personnalisés
2. créer de nouveaux générateurs

L'API pour 1) est assez fonctionnelle, mais elle est relativement récente, donc elle pourrait encore devoir évoluer dans les versions ultérieures du module `Random`. Par exemple, il est généralement suffisant d'implémenter une méthode `rand` pour que toutes les autres méthodes habituelles fonctionnent automatiquement.

L'API pour 2) est encore rudimentaire et peut nécessiter plus de travail que strictement nécessaire de la part de l'implémenteur, afin de prendre en charge les types habituels de valeurs générées.

### Generating random values of custom types

Générer des valeurs aléatoires pour certaines distributions peut impliquer divers compromis. *Les valeurs pré-calculées*, telles qu'un [alias table](https://en.wikipedia.org/wiki/Alias_method) pour les distributions discrètes, ou [“squeezing” functions](https://en.wikipedia.org/wiki/Rejection_sampling) pour les distributions univariées, peuvent considérablement accélérer l'échantillonnage. La quantité d'informations à pré-calculer peut dépendre du nombre de valeurs que nous prévoyons de tirer d'une distribution. De plus, certains générateurs de nombres aléatoires peuvent avoir certaines propriétés que divers algorithmes peuvent vouloir exploiter.

Le module `Random` définit un cadre personnalisable pour obtenir des valeurs aléatoires qui peuvent résoudre ces problèmes. Chaque invocation de `rand` génère un *échantillonneur* qui peut être personnalisé en tenant compte des compromis ci-dessus, en ajoutant des méthodes à `Sampler`, qui peut à son tour dispatcher sur le générateur de nombres aléatoires, l'objet qui caractérise la distribution, et une suggestion pour le nombre de répétitions. Actuellement, pour ce dernier, `Val{1}` (pour un seul échantillon) et `Val{Inf}` (pour un nombre arbitraire) sont utilisés, avec `Random.Repetition` comme alias pour les deux.

L'objet retourné par `Sampler` est ensuite utilisé pour générer les valeurs aléatoires. Lors de l'implémentation de l'interface de génération aléatoire pour une valeur `X` qui peut être échantillonnée, l'implémenteur doit définir la méthode

```julia
rand(rng, sampler)
```

pour le `sampler` particulier retourné par `Sampler(rng, X, repetition)`.

Les échantillonneurs peuvent être des valeurs arbitraires qui implémentent `rand(rng, sampler)`, mais pour la plupart des applications, les échantillonneurs prédéfinis suivants peuvent être suffisants :

1. `SamplerType{T}()` peut être utilisé pour implémenter des échantillonneurs qui tirent du type `T` (par exemple, `rand(Int)`). C'est le type par défaut retourné par `Sampler` pour les *types*.
2. `SamplerTrivial(self)` est un simple wrapper pour `self`, qui peut être accédé avec `[]`. C'est le sampler recommandé lorsque aucune information pré-calculée n'est nécessaire (par exemple, `rand(1:3)`), et c'est celui qui est retourné par défaut par `Sampler` pour *valeurs*.
3. `SamplerSimple(self, data)` contient également le champ `data` supplémentaire, qui peut être utilisé pour stocker des valeurs pré-calculées arbitraires, qui devraient être calculées dans une *méthode personnalisée* de `Sampler`.

Nous fournissons des exemples pour chacun de ceux-ci. Nous supposons ici que le choix de l'algorithme est indépendant du générateur de nombres aléatoires (RNG), donc nous utilisons `AbstractRNG` dans nos signatures.

```@docs
Random.Sampler
Random.SamplerType
Random.SamplerTrivial
Random.SamplerSimple
```

Le découplage de la pré-computation de la génération effective des valeurs fait partie de l'API et est également disponible pour l'utilisateur. Par exemple, supposons que `rand(rng, 1:20)` doive être appelé plusieurs fois dans une boucle : la manière de tirer parti de ce découplage est la suivante :

```julia
rng = Xoshiro()
sp = Random.Sampler(rng, 1:20) # or Random.Sampler(Xoshiro, 1:20)
for x in X
    n = rand(rng, sp) # similar to n = rand(rng, 1:20)
    # use n
end
```

C'est le mécanisme qui est également utilisé dans la bibliothèque standard, par exemple par l'implémentation par défaut de la génération de tableaux aléatoires (comme dans `rand(1:20, 10)`).

#### Generating values from a type

Étant donné un type `T`, on suppose actuellement que si `rand(T)` est défini, un objet de type `T` sera produit. `SamplerType` est le *sampler par défaut pour les types*. Afin de définir la génération aléatoire de valeurs de type `T`, la méthode `rand(rng::AbstractRNG, ::Random.SamplerType{T})` doit être définie et doit retourner des valeurs que `rand(rng, T)` est censé retourner.

Prenons l'exemple suivant : nous implémentons un type `Die`, avec un nombre variable `n` de faces, numérotées de `1` à `n`. Nous voulons que `rand(Die)` produise un `Die` avec un nombre aléatoire allant jusqu'à 20 faces (et au moins 4) :

```jldoctest Die
struct Die
    nsides::Int # number of sides
end

Random.rand(rng::AbstractRNG, ::Random.SamplerType{Die}) = Die(rand(rng, 4:20))

# output

```

Les méthodes scalaires et de tableau pour `Die` fonctionnent désormais comme prévu :

```jldoctest Die; setup = :(Random.seed!(1))
julia> rand(Die)
Die(5)

julia> rand(Xoshiro(0), Die)
Die(10)

julia> rand(Die, 3)
3-element Vector{Die}:
 Die(9)
 Die(15)
 Die(14)

julia> a = Vector{Die}(undef, 3); rand!(a)
3-element Vector{Die}:
 Die(19)
 Die(7)
 Die(17)
```

#### A simple sampler without pre-computed data

Ici, nous définissons un échantillonneur pour une collection. Si aucune donnée pré-calculée n'est requise, il peut être implémenté avec un échantillonneur `SamplerTrivial`, qui est en fait le *retour par défaut pour les valeurs*.

Pour définir la génération aléatoire à partir d'objets de type `S`, la méthode suivante doit être définie : `rand(rng::AbstractRNG, sp::Random.SamplerTrivial{S})`. Ici, `sp` enveloppe simplement un objet de type `S`, qui peut être accédé via `sp[]`. En continuant l'exemple du dé, nous voulons maintenant définir `rand(d::Die)` pour produire un `Int` correspondant à l'une des faces de `d` :

```jldoctest Die; setup = :(Random.seed!(1))
julia> Random.rand(rng::AbstractRNG, d::Random.SamplerTrivial{Die}) = rand(rng, 1:d[].nsides);

julia> rand(Die(4))
1

julia> rand(Die(4), 3)
3-element Vector{Any}:
 2
 3
 3
```

Étant donné un type de collection `S`, on suppose actuellement que si `rand(::S)` est défini, un objet de type `eltype(S)` sera produit. Dans le dernier exemple, un `Vector{Any}` est produit ; la raison en est que `eltype(Die) == Any`. Le remède consiste à définir `Base.eltype(::Type{Die}) = Int`.

#### Generating values for an `AbstractFloat` type

Les types `AbstractFloat` sont traités de manière spéciale, car par défaut, les valeurs aléatoires ne sont pas produites dans l'ensemble complet du type, mais plutôt dans `[0,1)`. La méthode suivante doit être implémentée pour `T <: AbstractFloat` : `Random.rand(::AbstractRNG, ::Random.SamplerTrivial{Random.CloseOpen01{T}})`

#### An optimized sampler with pre-computed data

Considérez une distribution discrète, où les nombres `1:n` sont tirés avec des probabilités données qui s'additionnent à un. Lorsque de nombreuses valeurs sont nécessaires à partir de cette distribution, la méthode la plus rapide consiste à utiliser un [alias table](https://en.wikipedia.org/wiki/Alias_method). Nous ne fournissons pas l'algorithme pour construire une telle table ici, mais supposons qu'il soit disponible dans `make_alias_table(probabilities)` à la place, et `draw_number(rng, alias_table)` peut être utilisé pour tirer un nombre aléatoire à partir de celle-ci.

Supposons que la distribution soit décrite par

```julia
struct DiscreteDistribution{V <: AbstractVector}
    probabilities::V
end
```

et que nous *voulons toujours* construire une table d'alias, peu importe le nombre de valeurs nécessaires (nous apprendrons à personnaliser cela ci-dessous). Les méthodes

```julia
Random.eltype(::Type{<:DiscreteDistribution}) = Int

function Random.Sampler(::Type{<:AbstractRNG}, distribution::DiscreteDistribution, ::Repetition)
    SamplerSimple(distribution, make_alias_table(distribution.probabilities))
end
```

devrait être défini pour retourner un échantillonneur avec des données pré-calculées, puis

```julia
function rand(rng::AbstractRNG, sp::SamplerSimple{<:DiscreteDistribution})
    draw_number(rng, sp.data)
end
```

sera utilisé pour dessiner les valeurs.

#### Custom sampler types

Le type `SamplerSimple` est suffisant pour la plupart des cas d'utilisation avec des données précalculées. Cependant, afin de démontrer comment utiliser des types de samplers personnalisés, nous implémentons ici quelque chose de similaire à `SamplerSimple`.

Revenons à notre exemple de `Die` : `rand(::Die)` utilise la génération aléatoire à partir d'une plage, donc il y a une opportunité pour cette optimisation. Nous appelons notre échantillonneur personnalisé `SamplerDie`.

```julia
import Random: Sampler, rand

struct SamplerDie <: Sampler{Int} # generates values of type Int
    die::Die
    sp::Sampler{Int} # this is an abstract type, so this could be improved
end

Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerDie(die, Sampler(RNG, 1:die.nsides, r))
# the `r` parameter will be explained later on

rand(rng::AbstractRNG, sp::SamplerDie) = rand(rng, sp.sp)
```

Il est maintenant possible d'obtenir un échantillonneur avec `sp = Sampler(rng, die)`, et d'utiliser `sp` au lieu de `die` dans tout appel `rand` impliquant `rng`. Dans l'exemple simpliste ci-dessus, `die` n'a pas besoin d'être stocké dans `SamplerDie`, mais c'est souvent le cas en pratique.

Bien sûr, ce modèle est si fréquent que le type d'assistance utilisé ci-dessus, à savoir `Random.SamplerSimple`, est disponible, nous évitant ainsi la définition de `SamplerDie` : nous aurions pu implémenter notre découplage avec :

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerSimple(die, Sampler(RNG, 1:die.nsides, r))

rand(rng::AbstractRNG, sp::SamplerSimple{Die}) = rand(rng, sp.data)
```

Ici, `sp.data` fait référence au deuxième paramètre dans l'appel au constructeur `SamplerSimple` (dans ce cas égal à `Sampler(rng, 1:die.nsides, r)`), tandis que l'objet `Die` peut être accédé via `sp[]`.

Comme `SamplerDie`, tout échantillonneur personnalisé doit être un sous-type de `Sampler{T}` où `T` est le type des valeurs générées. Notez que `SamplerSimple(x, data) isa Sampler{eltype(x)}`, ce qui limite ce que le premier argument de `SamplerSimple` peut être (il est recommandé d'utiliser `SamplerSimple` comme dans l'exemple `Die`, où `x` est simplement transmis lors de la définition d'une méthode `Sampler`). De même, `SamplerTrivial(x) isa Sampler{eltype(x)}`.

Un autre type d'assistance est actuellement disponible pour d'autres cas, `Random.SamplerTag`, mais est considéré comme une API interne et peut se briser à tout moment sans dépréciations appropriées.

#### Using distinct algorithms for scalar or array generation

Dans certains cas, que l'on souhaite générer seulement quelques valeurs ou un grand nombre de valeurs aura un impact sur le choix de l'algorithme. Cela est géré avec le troisième paramètre du constructeur `Sampler`. Supposons que nous ayons défini deux types d'assistance pour `Die`, disons `SamplerDie1` qui devrait être utilisé pour générer seulement quelques valeurs aléatoires, et `SamplerDieMany` pour de nombreuses valeurs. Nous pouvons utiliser ces types comme suit :

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{1}) = SamplerDie1(...)
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{Inf}) = SamplerDieMany(...)
```

Bien sûr, `rand` doit également être défini sur ces types (c'est-à-dire `rand(::AbstractRNG, ::SamplerDie1)` et `rand(::AbstractRNG, ::SamplerDieMany)`). Notez que, comme d'habitude, `SamplerTrivial` et `SamplerSimple` peuvent être utilisés si des types personnalisés ne sont pas nécessaires.

Remarque : `Sampler(rng, x)` est simplement un raccourci pour `Sampler(rng, x, Val(Inf))`, et `Random.Repetition` est un alias pour `Union{Val{1}, Val{Inf}}`.

### Creating new generators

L'API n'est pas encore clairement définie, mais en règle générale :

1. tout `rand` méthode produisant des types "de base" (`isbitstype` entier et types flottants dans `Base`) devrait être définie pour ce RNG spécifique, si nécessaire ;
2. d'autres méthodes `rand` documentées acceptant un `AbstractRNG` devraient fonctionner sans problème, (à condition que les méthodes de 1) sur lesquelles on s'appuie soient implémentées), mais peuvent bien sûr être spécialisées pour ce RNG s'il y a de la place pour l'optimisation ;
3. `copy` pour les pseudo-GRNs doit renvoyer une copie indépendante qui génère exactement la même séquence aléatoire que l'original à partir du moment où elle est appelée de la même manière. Lorsque cela n'est pas réalisable (par exemple, les GRNs basés sur du matériel), `copy` ne doit pas être implémenté.

Concernant 1), une méthode `rand` peut fonctionner automatiquement, mais elle n'est pas officiellement supportée et peut cesser de fonctionner sans avertissement dans une version ultérieure.

Pour définir une nouvelle méthode `rand` pour un générateur hypothétique `MyRNG`, et une spécification de valeur `s` (par exemple `s == Int`, ou `s == 1:10`) de type `S==typeof(s)` ou `S==Type{s}` si `s` est un type, les deux mêmes méthodes que nous avons vues auparavant doivent être définies :

1. `Sampler(::Type{MyRNG}, ::S, ::Repetition)`, qui renvoie un objet de type disons `SamplerS`
2. `rand(rng::MyRNG, sp::SamplerS)`

Il peut arriver que `Sampler(rng::AbstractRNG, ::S, ::Repetition)` soit déjà défini dans le module `Random`. Il serait alors possible de sauter l'étape 1) en pratique (si l'on souhaite spécialiser la génération pour ce type de RNG particulier), mais le type correspondant `SamplerS` est considéré comme un détail interne et peut être modifié sans avertissement.

#### Specializing array generation

Dans certains cas, pour un type de générateur de nombres aléatoires donné, générer un tableau de valeurs aléatoires peut être plus efficace avec une méthode spécialisée qu'en utilisant simplement la technique de découplage expliquée précédemment. C'est par exemple le cas pour `MersenneTwister`, qui écrit nativement des valeurs aléatoires dans un tableau.

Pour implémenter cette spécialisation pour `MyRNG` et pour une spécification `s`, produisant des éléments de type `S`, la méthode suivante peut être définie : `rand!(rng::MyRNG, a::AbstractArray{S}, ::SamplerS)`, où `SamplerS` est le type de l'échantillonneur retourné par `Sampler(MyRNG, s, Val(Inf))`. Au lieu de `AbstractArray`, il est possible d'implémenter la fonctionnalité uniquement pour un sous-type, par exemple `Array{S}`. La méthode de tableau non mutante de `rand` appellera automatiquement cette spécialisation en interne.

```@meta
DocTestSetup = nothing
```

# Reproducibility

En utilisant un paramètre RNG initialisé avec une graine donnée, vous pouvez reproduire la même séquence de nombres pseudorandom lorsque vous exécutez votre programme plusieurs fois. Cependant, une version mineure de Julia (par exemple, de 1.3 à 1.4) *peut changer* la séquence de nombres pseudorandom générés à partir d'une graine spécifique, en particulier si `MersenneTwister` est utilisé. (Même si la séquence produite par une fonction de bas niveau comme [`rand`](@ref) ne change pas, la sortie de fonctions de niveau supérieur comme [`randsubseq`](@ref) peut changer en raison des mises à jour d'algorithme.) Raison : garantir que les flux pseudorandom ne changent jamais interdit de nombreuses améliorations algorithmiques.

Si vous devez garantir la reproductibilité exacte des données aléatoires, il est conseillé de simplement *sauvegarder les données* (par exemple, en tant que pièce jointe supplémentaire dans une publication scientifique). (Vous pouvez également, bien sûr, spécifier une version particulière de Julia et un manifeste de package, surtout si vous exigez une reproductibilité au bit près.)

Les tests logiciels qui s'appuient sur des données "aléatoires" *spécifiques* devraient également généralement soit enregistrer les données, les intégrer dans le code de test, soit utiliser des packages tiers comme [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl). D'autre part, les tests qui devraient réussir pour des données aléatoires *la plupart du temps* (par exemple, tester `A \ (A*x) ≈ x` pour une matrice aléatoire `A = randn(n,n)`) peuvent utiliser un générateur de nombres aléatoires (RNG) avec une graine fixe pour s'assurer que le simple fait d'exécuter le test plusieurs fois ne rencontre pas un échec en raison de données très improbables (par exemple, une matrice extrêmement mal conditionnée).

La *distribution* statistique à partir de laquelle des échantillons aléatoires sont tirés *est* garantie d'être la même à travers toutes les petites versions de Julia.
