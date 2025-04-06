# [Types](@id man-types)

Les systèmes de types ont traditionnellement été classés en deux camps assez différents : les systèmes de types statiques, où chaque expression de programme doit avoir un type calculable avant l'exécution du programme, et les systèmes de types dynamiques, où rien n'est connu sur les types jusqu'à l'exécution, lorsque les valeurs réelles manipulées par le programme sont disponibles. L'orientation objet permet une certaine flexibilité dans les langages à typage statique en permettant d'écrire du code sans que les types précis des valeurs soient connus au moment de la compilation. La capacité d'écrire du code qui peut fonctionner sur différents types est appelée polymorphisme. Tout le code dans les langages dynamiquement typés classiques est polymorphe : ce n'est qu'en vérifiant explicitement les types, ou lorsque des objets ne parviennent pas à prendre en charge des opérations à l'exécution, que les types de valeurs sont jamais restreints.

Le système de types de Julia est dynamique, mais il tire certains des avantages des systèmes de types statiques en permettant d'indiquer que certaines valeurs sont de types spécifiques. Cela peut être d'une grande aide pour générer du code efficace, mais plus significativement, cela permet à l'appel de méthode basé sur les types des arguments de fonction d'être profondément intégré au langage. L'appel de méthode est exploré en détail dans [Methods](@ref), mais il est ancré dans le système de types présenté ici.

Le comportement par défaut en Julia lorsque les types sont omis est de permettre aux valeurs d'être de n'importe quel type. Ainsi, on peut écrire de nombreuses fonctions utiles en Julia sans jamais utiliser explicitement de types. Lorsque davantage d'expressivité est nécessaire, cependant, il est facile d'introduire progressivement des annotations de type explicites dans du code précédemment "non typé". L'ajout d'annotations sert trois objectifs principaux : tirer parti du puissant mécanisme de dispatch multiple de Julia, améliorer la lisibilité humaine et détecter les erreurs de programmation.

Décrire Julia dans le jargon de [type systems](https://en.wikipedia.org/wiki/Type_system), c'est : dynamique, nominatif et paramétrique. Les types génériques peuvent être paramétrés, et les relations hiérarchiques entre les types sont [explicitly declared](https://en.wikipedia.org/wiki/Nominal_type_system), plutôt que [implied by compatible structure](https://en.wikipedia.org/wiki/Structural_type_system). Une caractéristique particulièrement distinctive du système de types de Julia est que les types concrets ne peuvent pas être des sous-types les uns des autres : tous les types concrets sont finaux et ne peuvent avoir que des types abstraits comme super-types. Bien que cela puisse sembler au départ excessivement restrictif, cela a de nombreuses conséquences bénéfiques avec étonnamment peu d'inconvénients. Il s'avère qu'être capable d'hériter du comportement est beaucoup plus important qu'être capable d'hériter de la structure, et hériter des deux cause des difficultés significatives dans les langages orientés objet traditionnels. D'autres aspects de haut niveau du système de types de Julia qui devraient être mentionnés dès le départ sont :

  * Il n'y a pas de division entre les valeurs d'objet et les valeurs non-objet : toutes les valeurs en Julia sont de véritables objets ayant un type qui appartient à un seul graphe de types entièrement connecté, tous les nœuds de ce graphe étant également de première classe en tant que types.
  * Il n'y a pas de concept significatif de "type à la compilation" : le seul type qu'une valeur a est son type réel lorsque le programme s'exécute. Cela s'appelle un "type à l'exécution" dans les langages orientés objet où la combinaison de la compilation statique avec le polymorphisme rend cette distinction significative.
  * Seules les valeurs, pas les variables, ont des types – les variables ne sont que des noms liés à des valeurs, bien que pour simplifier, nous puissions dire "type d'une variable" comme abréviation pour "type de la valeur à laquelle une variable fait référence".
  * Les types abstraits et concrets peuvent être paramétrés par d'autres types. Ils peuvent également être paramétrés par des symboles, par des valeurs de tout type pour lequel [`isbits`](@ref) renvoie vrai (essentiellement, des choses comme des nombres et des booléens qui sont stockés comme des types C ou des `struct`s sans pointeurs vers d'autres objets), et aussi par des tuples de ceux-ci. Les paramètres de type peuvent être omis lorsqu'ils n'ont pas besoin d'être référencés ou restreints.

Le système de types de Julia est conçu pour être puissant et expressif, tout en étant clair, intuitif et discret. De nombreux programmeurs Julia peuvent ne jamais ressentir le besoin d'écrire du code qui utilise explicitement des types. Cependant, certains types de programmation deviennent plus clairs, plus simples, plus rapides et plus robustes avec des types déclarés.

## Type Declarations

L'opérateur `::` peut être utilisé pour attacher des annotations de type aux expressions et aux variables dans les programmes. Il y a deux raisons principales de le faire :

1. En tant qu'affirmation pour aider à confirmer que votre programme fonctionne comme vous l'attendez, et
2. Pour fournir des informations de type supplémentaires au compilateur, ce qui peut ensuite améliorer les performances dans certains cas.

Lorsqu'il est ajouté à une expression calculant une valeur, l'opérateur `::` est lu comme "est une instance de". Il peut être utilisé n'importe où pour affirmer que la valeur de l'expression à gauche est une instance du type à droite. Lorsque le type à droite est concret, la valeur à gauche doit avoir ce type comme son implémentation – rappelez-vous que tous les types concrets sont finaux, donc aucune implémentation n'est un sous-type d'une autre. Lorsque le type est abstrait, il suffit que la valeur soit implémentée par un type concret qui est un sous-type du type abstrait. Si l'assertion de type n'est pas vraie, une exception est levée, sinon, la valeur de gauche est retournée :

```jldoctest
julia> (1+2)::AbstractFloat
ERROR: TypeError: in typeassert, expected AbstractFloat, got a value of type Int64

julia> (1+2)::Int
3
```

Cela permet d'attacher une assertion de type à n'importe quelle expression sur place.

Lorsqu'il est ajouté à une variable sur le côté gauche d'une affectation, ou dans le cadre d'une déclaration `local`, l'opérateur `::` signifie quelque chose d'un peu différent : il déclare que la variable doit toujours avoir le type spécifié, comme une déclaration de type dans un langage à typage statique tel que C. Chaque valeur assignée à la variable sera convertie au type déclaré en utilisant [`convert`](@ref) :

```jldoctest
julia> function foo()
           x::Int8 = 100
           x
       end
foo (generic function with 1 method)

julia> x = foo()
100

julia> typeof(x)
Int8
```

Cette fonctionnalité est utile pour éviter les "pièges" de performance qui pourraient survenir si l'une des affectations à une variable changeait son type de manière inattendue.

Ce comportement de "déclaration" ne se produit que dans des contextes spécifiques :

```julia
local x::Int8  # in a local declaration
x::Int8 = 10   # as the left-hand side of an assignment
```

et s'applique à l'ensemble du champ actuel, même avant la déclaration.

À partir de Julia 1.8, les déclarations de type peuvent désormais être utilisées dans le scope global, c'est-à-dire que des annotations de type peuvent être ajoutées aux variables globales pour rendre leur accès stable en termes de type.

```julia
julia> x::Int = 10
10

julia> x = 3.5
ERROR: InexactError: Int64(3.5)

julia> function foo(y)
           global x = 15.8    # throws an error when foo is called
           return x + y
       end
foo (generic function with 1 method)

julia> foo(10)
ERROR: InexactError: Int64(15.8)
```

Les déclarations peuvent également être attachées aux définitions de fonction :

```julia
function sinc(x)::Float64
    if x == 0
        return 1
    end
    return sin(pi*x)/(pi*x)
end
```

Le retour de cette fonction se comporte exactement comme une affectation à une variable avec un type déclaré : la valeur est toujours convertie en `Float64`.

## [Abstract Types](@id man-abstract-types)

Les types abstraits ne peuvent pas être instanciés et servent uniquement de nœuds dans le graphe des types, décrivant ainsi des ensembles de types concrets liés : ces types concrets qui en sont les descendants. Nous commençons par les types abstraits bien qu'ils n'aient pas d'instanciation, car ils constituent la colonne vertébrale du système de types : ils forment la hiérarchie conceptuelle qui rend le système de types de Julia plus qu'une simple collection d'implémentations d'objets.

Rappelez-vous que dans [Integers and Floating-Point Numbers](@ref), nous avons introduit une variété de types concrets de valeurs numériques : [`Int8`](@ref), [`UInt8`](@ref), [`Int16`](@ref), [`UInt16`](@ref), [`Int32`](@ref), [`UInt32`](@ref), [`Int64`](@ref), [`UInt64`](@ref), [`Int128`](@ref), [`UInt128`](@ref), [`Float16`](@ref), [`Float32`](@ref), et [`Float64`](@ref). Bien qu'ils aient des tailles de représentation différentes, `Int8`, `Int16`, `Int32`, `Int64` et `Int128` ont tous en commun d'être des types d'entiers signés. De même, `UInt8`, `UInt16`, `UInt32`, `UInt64` et `UInt128` sont tous des types d'entiers non signés, tandis que `Float16`, `Float32` et `Float64` se distinguent en étant des types à virgule flottante plutôt que des entiers. Il est courant qu'un morceau de code ait du sens, par exemple, uniquement si ses arguments sont une sorte d'entier, mais ne dépendent pas vraiment de quel *type* particulier d'entier. Par exemple, l'algorithme du plus grand commun diviseur fonctionne pour tous les types d'entiers, mais ne fonctionnera pas pour les nombres à virgule flottante. Les types abstraits permettent la construction d'une hiérarchie de types, fournissant un contexte dans lequel des types concrets peuvent s'adapter. Cela vous permet, par exemple, de programmer facilement pour tout type qui est un entier, sans restreindre un algorithme à un type spécifique d'entier.

Les types abstraits sont déclarés en utilisant le mot-clé [`abstract type`](@ref). Les syntaxes générales pour déclarer un type abstrait sont :

```
abstract type «name» end
abstract type «name» <: «supertype» end
```

Le mot-clé `abstract type` introduit un nouveau type abstrait, dont le nom est donné par `«name»`. Ce nom peut être suivi en option par [`<:`](@ref) et un type déjà existant, indiquant que le type abstrait nouvellement déclaré est un sous-type de ce type "parent".

Lorsque aucun supertype n'est donné, le supertype par défaut est `Any` – un type abstrait prédéfini dont tous les objets sont des instances et tous les types sont des sous-types. En théorie des types, `Any` est communément appelé "top" car il est au sommet du graphe des types. Julia a également un type abstrait "bottom" prédéfini, au nadir du graphe des types, qui est écrit comme `Union{}`. C'est l'exact opposé de `Any` : aucun objet n'est une instance de `Union{}` et tous les types sont des supertypes de `Union{}`.

Considérons certains des types abstraits qui composent la hiérarchie numérique de Julia :

```julia
abstract type Number end
abstract type Real          <: Number end
abstract type AbstractFloat <: Real end
abstract type Integer       <: Real end
abstract type Signed        <: Integer end
abstract type Unsigned      <: Integer end
```

Le type [`Number`](@ref) est un type enfant direct de `Any`, et [`Real`](@ref) est son enfant. À son tour, `Real` a deux enfants (il en a plus, mais seulement deux sont montrés ici ; nous aborderons les autres plus tard) : [`Integer`](@ref) et [`AbstractFloat`](@ref), séparant le monde en représentations d'entiers et représentations de nombres réels. Les représentations de nombres réels incluent des types à virgule flottante, mais incluent également d'autres types, tels que les rationnels. `AbstractFloat` inclut uniquement des représentations à virgule flottante de nombres réels. Les entiers sont en outre subdivisés en variétés [`Signed`](@ref) et [`Unsigned`](@ref).

L'opérateur `<:` signifie généralement "est un sous-type de", et, utilisé dans des déclarations comme celles ci-dessus, déclare le type à droite comme étant un supertype immédiat du type nouvellement déclaré. Il peut également être utilisé dans des expressions comme un opérateur de sous-type qui renvoie `true` lorsque son opérande gauche est un sous-type de son opérande droit :

```jldoctest
julia> Integer <: Number
true

julia> Integer <: AbstractFloat
false
```

Un usage important des types abstraits est de fournir des implémentations par défaut pour les types concrets. Pour donner un exemple simple, considérons :

```julia
function myplus(x,y)
    x+y
end
```

La première chose à noter est que les déclarations d'arguments ci-dessus sont équivalentes à `x::Any` et `y::Any`. Lorsque cette fonction est invoquée, par exemple en tant que `myplus(2,5)`, le répartiteur choisit la méthode la plus spécifique nommée `myplus` qui correspond aux arguments donnés. (Voir [Methods](@ref) pour plus d'informations sur le dispatch multiple.)

En supposant qu'aucune méthode plus spécifique que celle ci-dessus ne soit trouvée, Julia définit et compile ensuite en interne une méthode appelée `myplus` spécifiquement pour deux arguments `Int` basée sur la fonction générique donnée ci-dessus, c'est-à-dire qu'elle définit et compile implicitement :

```julia
function myplus(x::Int,y::Int)
    x+y
end
```

et enfin, cela invoque cette méthode spécifique.

Ainsi, les types abstraits permettent aux programmeurs d'écrire des fonctions génériques qui peuvent ensuite être utilisées comme méthode par défaut par de nombreuses combinaisons de types concrets. Grâce au dispatch multiple, le programmeur a un contrôle total sur l'utilisation de la méthode par défaut ou d'une méthode plus spécifique.

Un point important à noter est qu'il n'y a aucune perte de performance si le programmeur s'appuie sur une fonction dont les arguments sont des types abstraits, car elle est recompilée pour chaque tuple de types d'arguments concrets avec lequel elle est invoquée. (Il peut cependant y avoir un problème de performance dans le cas des arguments de fonction qui sont des conteneurs de types abstraits ; voir [Performance Tips](@ref man-performance-abstract-container).)

## Primitive Types

!!! warning
    Il est presque toujours préférable d'encapsuler un type primitif existant dans un nouveau type composite plutôt que de définir votre propre type primitif.

    Cette fonctionnalité existe pour permettre à Julia de démarrer les types primitifs standard que prend en charge LLVM. Une fois qu'ils sont définis, il y a très peu de raisons de définir d'autres types.


Un type primitif est un type concret dont les données consistent en de simples bits. Des exemples classiques de types primitifs sont les entiers et les valeurs à virgule flottante. Contrairement à la plupart des langages, Julia vous permet de déclarer vos propres types primitifs, plutôt que de ne fournir qu'un ensemble fixe de types intégrés. En fait, les types primitifs standard sont tous définis dans le langage lui-même :

```julia
primitive type Float16 <: AbstractFloat 16 end
primitive type Float32 <: AbstractFloat 32 end
primitive type Float64 <: AbstractFloat 64 end

primitive type Bool <: Integer 8 end
primitive type Char <: AbstractChar 32 end

primitive type Int8    <: Signed   8 end
primitive type UInt8   <: Unsigned 8 end
primitive type Int16   <: Signed   16 end
primitive type UInt16  <: Unsigned 16 end
primitive type Int32   <: Signed   32 end
primitive type UInt32  <: Unsigned 32 end
primitive type Int64   <: Signed   64 end
primitive type UInt64  <: Unsigned 64 end
primitive type Int128  <: Signed   128 end
primitive type UInt128 <: Unsigned 128 end
```

Les syntaxes générales pour déclarer un type primitif sont :

```
primitive type «name» «bits» end
primitive type «name» <: «supertype» «bits» end
```

Le nombre de bits indique combien d'espace de stockage le type nécessite et le nom donne un nom au nouveau type. Un type primitif peut être déclaré en option comme un sous-type d'un supertype. Si un supertype est omis, alors le type par défaut a `Any` comme son supertype immédiat. La déclaration de [`Bool`](@ref) ci-dessus signifie donc qu'une valeur booléenne prend huit bits à stocker, et a [`Integer`](@ref) comme son supertype immédiat. Actuellement, seules les tailles qui sont des multiples de 8 bits sont prises en charge et vous êtes susceptible de rencontrer des bugs LLVM avec des tailles autres que celles utilisées ci-dessus. Par conséquent, les valeurs booléennes, bien qu'elles aient réellement besoin d'un seul bit, ne peuvent pas être déclarées comme étant plus petites que huit bits.

Les types [`Bool`](@ref), [`Int8`](@ref) et [`UInt8`](@ref) ont tous des représentations identiques : ce sont des morceaux de mémoire de huit bits. Cependant, comme le système de types de Julia est nominatif, ils ne sont pas interchangeables malgré leur structure identique. Une différence fondamentale entre eux est qu'ils ont des supertypes différents : le supertype direct de `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` est [`Integer`](@ref), celui de `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` est [`Signed`](@ref), et celui de `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` est [`Unsigned`](@ref). Toutes les autres différences entre `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566`, `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` et `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566` concernent le comportement – la façon dont les fonctions sont définies pour agir lorsqu'elles reçoivent des objets de ces types comme arguments. C'est pourquoi un système de types nominatif est nécessaire : si la structure déterminait le type, qui à son tour dicte le comportement, alors il serait impossible de faire en sorte que `4d61726b646f776e2e436f64652822222c2022426f6f6c2229_40726566` se comporte différemment de `4d61726b646f776e2e436f64652822222c2022496e74382229_40726566` ou `4d61726b646f776e2e436f64652822222c202255496e74382229_40726566`.

## Composite Types

[Composite types](https://en.wikipedia.org/wiki/Composite_data_type) sont appelés enregistrements, structures ou objets dans divers langages. Un type composite est une collection de champs nommés, dont une instance peut être traitée comme une seule valeur. Dans de nombreux langages, les types composites sont le seul type définissable par l'utilisateur, et ils sont de loin le type défini par l'utilisateur le plus couramment utilisé dans Julia également.

Dans les langages orientés objet mainstream, tels que C++, Java, Python et Ruby, les types composites ont également des fonctions nommées qui leur sont associées, et la combinaison est appelée un "objet". Dans des langages orientés objet plus purs, tels que Ruby ou Smalltalk, toutes les valeurs sont des objets, qu'elles soient composites ou non. Dans des langages orientés objet moins purs, y compris C++ et Java, certaines valeurs, telles que les entiers et les valeurs à virgule flottante, ne sont pas des objets, tandis que les instances de types composites définis par l'utilisateur sont de véritables objets avec des méthodes associées. Dans Julia, toutes les valeurs sont des objets, mais les fonctions ne sont pas regroupées avec les objets sur lesquels elles opèrent. Cela est nécessaire puisque Julia choisit quelle méthode d'une fonction utiliser par dispatch multiple, ce qui signifie que les types de *tous* les arguments d'une fonction sont pris en compte lors de la sélection d'une méthode, plutôt que seulement le premier (voir [Methods](@ref) pour plus d'informations sur les méthodes et le dispatch). Ainsi, il serait inapproprié que les fonctions "appartiennent" uniquement à leur premier argument. Organiser les méthodes en objets fonctionnels plutôt que d'avoir des sacs de méthodes nommés "à l'intérieur" de chaque objet s'avère être un aspect très bénéfique de la conception du langage.

Les types composites sont introduits avec le mot-clé [`struct`](@ref) suivi d'un bloc de noms de champs, éventuellement annotés avec des types en utilisant l'opérateur `::` :

```jldoctest footype
julia> struct Foo
           bar
           baz::Int
           qux::Float64
       end
```

Les champs sans annotation de type par défaut sont de type `Any`, et peuvent donc contenir n'importe quel type de valeur.

De nouveaux objets de type `Foo` sont créés en appliquant l'objet de type `Foo` comme une fonction aux valeurs de ses champs :

```jldoctest footype
julia> foo = Foo("Hello, world.", 23, 1.5)
Foo("Hello, world.", 23, 1.5)

julia> typeof(foo)
Foo
```

Lorsqu'un type est appliqué comme une fonction, on l'appelle un *constructeur*. Deux constructeurs sont générés automatiquement (ceux-ci sont appelés *constructeurs par défaut*). L'un accepte n'importe quel argument et appelle [`convert`](@ref) pour les convertir en types des champs, et l'autre accepte des arguments qui correspondent exactement aux types des champs. La raison pour laquelle ces deux constructeurs sont générés est que cela facilite l'ajout de nouvelles définitions sans remplacer involontairement un constructeur par défaut.

Puisque le champ `bar` n'est pas contraint en type, n'importe quelle valeur fera l'affaire. Cependant, la valeur de `baz` doit être convertible en `Int` :

```jldoctest footype
julia> Foo((), 23.5, 1)
ERROR: InexactError: Int64(23.5)
Stacktrace:
[...]
```

Vous pouvez trouver une liste de noms de champs en utilisant la fonction [`fieldnames`](@ref).

```jldoctest footype
julia> fieldnames(Foo)
(:bar, :baz, :qux)
```

Vous pouvez accéder aux valeurs des champs d'un objet composite en utilisant la notation traditionnelle `foo.bar` :

```jldoctest footype
julia> foo.bar
"Hello, world."

julia> foo.baz
23

julia> foo.qux
1.5
```

Les objets composites déclarés avec `struct` sont *immuables* ; ils ne peuvent pas être modifiés après leur construction. Cela peut sembler étrange au début, mais cela présente plusieurs avantages :

  * Il peut être plus efficace. Certaines structures peuvent être compactées efficacement dans des tableaux, et dans certains cas, le compilateur est capable d'éviter d'allouer des objets immuables entièrement.
  * Il n'est pas possible de violer les invariants fournis par les constructeurs du type.
  * Le code utilisant des objets immuables peut être plus facile à comprendre.

Un objet immuable peut contenir des objets mutables, tels que des tableaux, en tant que champs. Ces objets contenus resteront mutables ; seuls les champs de l'objet immuable lui-même ne peuvent pas être modifiés pour pointer vers d'autres objets.

Là où cela est nécessaire, des objets composites mutables peuvent être déclarés avec le mot-clé [`mutable struct`](@ref), qui sera discuté dans la section suivante.

Si tous les champs d'une structure immuable sont indistinguables (`===`), alors deux valeurs immuables contenant ces champs sont également indistinguables :

```jldoctest
julia> struct X
           a::Int
           b::Float64
       end

julia> X(1, 2) === X(1, 2)
true
```

Il y a beaucoup plus à dire sur la façon dont les instances de types composites sont créées, mais cette discussion dépend à la fois de [Parametric Types](@ref) et de [Methods](@ref), et est suffisamment importante pour être abordée dans sa propre section : [Constructors](@ref man-constructors).

Pour de nombreux types définis par l'utilisateur `X`, vous pouvez vouloir définir une méthode [`Base.broadcastable(x::X) = Ref(x)`](@ref man-interfaces-broadcasting) afin que les instances de ce type agissent comme des "scalaires" à 0 dimensions pour [broadcasting](@ref Broadcasting).

## Mutable Composite Types

Si un type composite est déclaré avec `mutable struct` au lieu de `struct`, alors les instances de celui-ci peuvent être modifiées :

```jldoctest bartype
julia> mutable struct Bar
           baz
           qux::Float64
       end

julia> bar = Bar("Hello", 1.5);

julia> bar.qux = 2.0
2.0

julia> bar.baz = 1//2
1//2
```

Une interface supplémentaire entre les champs et l'utilisateur peut être fournie via [Instance Properties](@ref man-instance-properties). Cela accorde plus de contrôle sur ce qui peut être accessible et modifié en utilisant la notation `bar.baz`.

Pour prendre en charge la mutation, de tels objets sont généralement alloués sur le tas et ont des adresses mémoire stables. Un objet mutable est comme un petit conteneur qui peut contenir différentes valeurs au fil du temps, et ne peut donc être identifié de manière fiable qu'avec son adresse. En revanche, une instance d'un type immuable est associée à des valeurs de champ spécifiques – les valeurs de champ seules vous disent tout sur l'objet. En décidant de rendre un type mutable, demandez-vous si deux instances avec les mêmes valeurs de champ seraient considérées comme identiques, ou si elles pourraient avoir besoin de changer indépendamment au fil du temps. Si elles seraient considérées comme identiques, le type devrait probablement être immuable.

Pour résumer, deux propriétés essentielles définissent l'immuabilité en Julia :

  * Il n'est pas permis de modifier la valeur d'un type immuable.

      * Pour les types de bits, cela signifie que le motif de bits d'une valeur une fois défini ne changera jamais et que cette valeur est l'identité d'un type de bits.
      * Pour les types composites, cela signifie que l'identité des valeurs de ses champs ne changera jamais. Lorsque les champs sont de types bits, cela signifie que leurs bits ne changeront jamais. Pour les champs dont les valeurs sont des types mutables comme les tableaux, cela signifie que les champs référeront toujours à la même valeur mutable même si le contenu de cette valeur mutable peut lui-même être modifié.
  * Un objet avec un type immuable peut être copié librement par le compilateur puisque son immutabilité rend impossible de distinguer programmatique entre l'objet original et une copie.

      * En particulier, cela signifie que des valeurs immuables suffisamment petites comme les entiers et les flottants sont généralement passées aux fonctions dans des registres (ou allouées sur la pile).
      * Les valeurs mutables, en revanche, sont allouées sur le tas et passées aux fonctions sous forme de pointeurs vers des valeurs allouées sur le tas, sauf dans les cas où le compilateur est certain qu'il n'y a aucun moyen de dire que ce n'est pas ce qui se passe.

Dans les cas où un ou plusieurs champs d'une structure mutable par ailleurs sont connus pour être immuables, on peut déclarer ces champs comme tels en utilisant `const` comme montré ci-dessous. Cela permet certaines, mais pas toutes les optimisations des structures immuables, et peut être utilisé pour faire respecter des invariants sur les champs particuliers marqués comme `const`.

!!! compat "Julia 1.8"
    `const` annoter les champs de structures mutables nécessite au moins Julia 1.8.


```jldoctest baztype
julia> mutable struct Baz
           a::Int
           const b::Float64
       end

julia> baz = Baz(1, 1.5);

julia> baz.a = 2
2

julia> baz.b = 2.0
ERROR: setfield!: const field .b of type Baz cannot be changed
[...]
```

## [Declared Types](@id man-declared-types)

Les trois types (abstrait, primitif, composite) discutés dans les sections précédentes sont en réalité tous étroitement liés. Ils partagent les mêmes propriétés clés :

  * Ils sont explicitement déclarés.
  * Ils ont des noms.
  * Ils ont explicitement déclaré des supertypes.
  * Ils peuvent avoir des paramètres.

En raison de ces propriétés partagées, ces types sont représentés en interne comme des instances du même concept, `DataType`, qui est le type de l'un de ces types :

```jldoctest
julia> typeof(Real)
DataType

julia> typeof(Int)
DataType
```

Un `DataType` peut être abstrait ou concret. S'il est concret, il a une taille spécifiée, une disposition de stockage et (optionnellement) des noms de champs. Ainsi, un type primitif est un `DataType` avec une taille non nulle, mais sans noms de champs. Un type composite est un `DataType` qui a des noms de champs ou est vide (taille nulle).

Chaque valeur concrète dans le système est une instance d'un `DataType`.

## Type Unions

Un type union est un type abstrait spécial qui inclut comme objets toutes les instances de n'importe lequel de ses types d'argument, construit en utilisant le mot-clé spécial [`Union`](@ref) :

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 :: IntOrString
1

julia> "Hello!" :: IntOrString
"Hello!"

julia> 1.0 :: IntOrString
ERROR: TypeError: in typeassert, expected Union{Int64, AbstractString}, got a value of type Float64
```

Les compilateurs pour de nombreux langages ont une construction d'union interne pour raisonner sur les types ; Julia l'expose simplement au programmeur. Le compilateur Julia est capable de générer un code efficace en présence de types `Union` avec un petit nombre de types [^1], en générant un code spécialisé dans des branches séparées pour chaque type possible.

Un cas particulièrement utile d'un type `Union` est `Union{T, Nothing}`, où `T` peut être n'importe quel type et [`Nothing`](@ref) est le type singleton dont la seule instance est l'objet [`nothing`](@ref). Ce modèle est l'équivalent Julia de [`Nullable`, `Option` or `Maybe`](https://en.wikipedia.org/wiki/Nullable_type) types dans d'autres langages. Déclarer un argument de fonction ou un champ comme `Union{T, Nothing}` permet de le définir soit à une valeur de type `T`, soit à `nothing` pour indiquer qu'il n'y a pas de valeur. Voir [this FAQ entry](@ref faq-nothing) pour plus d'informations.

## Parametric Types

Une caractéristique importante et puissante du système de types de Julia est qu'il est paramétrique : les types peuvent prendre des paramètres, de sorte que les déclarations de types introduisent en réalité toute une famille de nouveaux types – un pour chaque combinaison possible de valeurs de paramètres. Il existe de nombreux langages qui prennent en charge une version de [generic programming](https://en.wikipedia.org/wiki/Generic_programming), dans lequel des structures de données et des algorithmes pour les manipuler peuvent être spécifiés sans spécifier les types exacts impliqués. Par exemple, une forme de programmation générique existe dans ML, Haskell, Ada, Eiffel, C++, Java, C#, F# et Scala, pour n'en nommer que quelques-uns. Certains de ces langages prennent en charge le véritable polymorphisme paramétrique (par exemple, ML, Haskell, Scala), tandis que d'autres prennent en charge des styles de programmation générique ad-hoc, basés sur des modèles (par exemple, C++, Java). Avec tant de variétés différentes de programmation générique et de types paramétriques dans divers langages, nous n'allons même pas essayer de comparer les types paramétriques de Julia à d'autres langages, mais nous allons plutôt nous concentrer sur l'explication du système de Julia en tant que tel. Nous noterons cependant que, parce que Julia est un langage à typage dynamique et n'a pas besoin de prendre toutes les décisions de type au moment de la compilation, de nombreuses difficultés traditionnelles rencontrées dans les systèmes de types paramétriques statiques peuvent être relativement facilement gérées.

Tous les types déclarés (la variété `DataType`) peuvent être paramétrés, avec la même syntaxe dans chaque cas. Nous les discuterons dans l'ordre suivant : d'abord, les types composites paramétriques, puis les types abstraits paramétriques, et enfin les types primitifs paramétriques.

### [Parametric Composite Types](@id man-parametric-composite-types)

Les paramètres de type sont introduits immédiatement après le nom du type, entourés d'accolades :

```jldoctest pointtype
julia> struct Point{T}
           x::T
           y::T
       end
```

Cette déclaration définit un nouveau type paramétrique, `Point{T}`, contenant deux "coordonnées" de type `T`. Que peut-on demander, qu'est-ce que `T` ? Eh bien, c'est précisément le but des types paramétriques : cela peut être n'importe quel type (ou une valeur de n'importe quel type de bits, en fait, bien que ici, il soit clairement utilisé comme un type). `Point{Float64}` est un type concret équivalent au type défini en remplaçant `T` dans la définition de `Point` par [`Float64`](@ref). Ainsi, cette seule déclaration déclare en réalité un nombre illimité de types : `Point{Float64}`, `Point{AbstractString}`, `Point{Int64}`, etc. Chacun de ces types est maintenant un type concret utilisable :

```jldoctest pointtype
julia> Point{Float64}
Point{Float64}

julia> Point{AbstractString}
Point{AbstractString}
```

Le type `Point{Float64}` est un point dont les coordonnées sont des valeurs à virgule flottante de 64 bits, tandis que le type `Point{AbstractString}` est un "point" dont les "coordonnées" sont des objets de chaîne de caractères (voir [Strings](@ref)).

`Point` lui-même est également un type d'objet valide, contenant toutes les instances `Point{Float64}`, `Point{AbstractString}`, etc. en tant que sous-types :

```jldoctest pointtype
julia> Point{Float64} <: Point
true

julia> Point{AbstractString} <: Point
true
```

D'autres types, bien sûr, ne sont pas des sous-types de celui-ci :

```jldoctest pointtype
julia> Float64 <: Point
false

julia> AbstractString <: Point
false
```

Les types `Point` concrets avec différentes valeurs de `T` ne sont jamais des sous-types les uns des autres :

```jldoctest pointtype
julia> Point{Float64} <: Point{Int64}
false

julia> Point{Float64} <: Point{Real}
false
```

!!! warning
    Ce dernier point est *très* important : même si `Float64 <: Real`, nous **N'AVONS PAS** `Point{Float64} <: Point{Real}`.


En d'autres termes, dans le jargon de la théorie des types, les paramètres de type de Julia sont *invariants*, plutôt que d'être [covariant (or even contravariant)](https://en.wikipedia.org/wiki/Covariance_and_contravariance_%28computer_science%29). Cela pour des raisons pratiques : bien qu'une instance de `Point{Float64}` puisse conceptuellement être semblable à une instance de `Point{Real}`, les deux types ont des représentations différentes en mémoire :

  * Une instance de `Point{Float64}` peut être représentée de manière compacte et efficace comme une paire immédiate de valeurs de 64 bits ;
  * Une instance de `Point{Real}` doit être capable de contenir n'importe quelle paire d'instances de [`Real`](@ref). Étant donné que les objets qui sont des instances de `Real` peuvent avoir une taille et une structure arbitraires, en pratique, une instance de `Point{Real}` doit être représentée comme une paire de pointeurs vers des objets `Real` alloués individuellement.

L'efficacité gagnée en pouvant stocker des objets `Point{Float64}` avec des valeurs immédiates est considérablement amplifiée dans le cas des tableaux : un `Array{Float64}` peut être stocké comme un bloc de mémoire contigu de valeurs flottantes de 64 bits, tandis qu'un `Array{Real}` doit être un tableau de pointeurs vers des objets [`Real`](@ref) alloués individuellement – qui peuvent très bien être des valeurs flottantes de 64 bits [boxed](https://en.wikipedia.org/wiki/Object_type_%28object-oriented_programming%29#Boxing), mais qui peuvent également être des objets complexes de taille arbitraire, qui sont déclarés comme des implémentations du type abstrait `Real`.

Puisque `Point{Float64}` n'est pas un sous-type de `Point{Real}`, la méthode suivante ne peut pas être appliquée aux arguments de type `Point{Float64}` :

```julia
function norm(p::Point{Real})
    sqrt(p.x^2 + p.y^2)
end
```

Une manière correcte de définir une méthode qui accepte tous les arguments de type `Point{T}` où `T` est un sous-type de [`Real`](@ref) est :

```julia
function norm(p::Point{<:Real})
    sqrt(p.x^2 + p.y^2)
end
```

(Équivalemment, on pourrait définir `function norm(p::Point{T} where T<:Real)` ou `function norm(p::Point{T}) where T<:Real` ; voir [UnionAll Types](@ref).)

D'autres exemples seront discutés plus tard dans [Methods](@ref).

Comment construit-on un objet `Point` ? Il est possible de définir des constructeurs personnalisés pour les types composites, qui seront discutés en détail dans [Constructors](@ref man-constructors), mais en l'absence de déclarations de constructeur spéciales, il existe deux façons par défaut de créer de nouveaux objets composites, l'une dans laquelle les paramètres de type sont explicitement donnés et l'autre dans laquelle ils sont implicites par les arguments du constructeur d'objet.

Since the type `Point{Float64}` is a concrete type equivalent to `Point` declared with [`Float64`](@ref) in place of `T`, it can be applied as a constructor accordingly:

```jldoctest pointtype
julia> p = Point{Float64}(1.0, 2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p)
Point{Float64}
```

Pour le constructeur par défaut, exactement un argument doit être fourni pour chaque champ :

```jldoctest pointtype
julia> Point{Float64}(1.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]

julia> Point{Float64}(1.0, 2.0, 3.0)
ERROR: MethodError: no method matching Point{Float64}(::Float64, ::Float64, ::Float64)
The type `Point{Float64}` exists, but no method is defined for this combination of argument types when trying to construct it.
[...]
```

Un seul constructeur par défaut est généré pour les types paramétriques, car il n'est pas possible de le remplacer. Ce constructeur accepte n'importe quel argument et les convertit en types de champ.

Dans de nombreux cas, il est redondant de fournir le type de l'objet `Point` que l'on souhaite construire, car les types des arguments de l'appel au constructeur fournissent déjà des informations de type implicites. Pour cette raison, vous pouvez également appliquer `Point` lui-même comme constructeur, à condition que la valeur implicite du type de paramètre `T` soit sans ambiguïté :

```jldoctest pointtype
julia> p1 = Point(1.0,2.0)
Point{Float64}(1.0, 2.0)

julia> typeof(p1)
Point{Float64}

julia> p2 = Point(1,2)
Point{Int64}(1, 2)

julia> typeof(p2)
Point{Int64}
```

Dans le cas de `Point`, le type de `T` est clairement implicite si et seulement si les deux arguments de `Point` ont le même type. Lorsque ce n'est pas le cas, le constructeur échouera avec un [`MethodError`](@ref) :

```jldoctest pointtype
julia> Point(1,2.5)
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T
   @ Main none:2

Stacktrace:
[...]
```

Des méthodes de constructeur pour gérer correctement de tels cas mixtes peuvent être définies, mais cela ne sera pas discuté avant plus tard dans [Constructors](@ref man-constructors).

### Parametric Abstract Types

Les déclarations de types abstraits paramétriques déclarent une collection de types abstraits, de la même manière :

```jldoctest pointytype
julia> abstract type Pointy{T} end
```

Avec cette déclaration, `Pointy{T}` est un type abstrait distinct pour chaque type ou valeur entière de `T`. Comme avec les types composites paramétriques, chaque instance de ce type est un sous-type de `Pointy` :

```jldoctest pointytype
julia> Pointy{Int64} <: Pointy
true

julia> Pointy{1} <: Pointy
true
```

Les types abstraits paramétriques sont invariants, tout comme les types composites paramétriques :

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{Real}
false

julia> Pointy{Real} <: Pointy{Float64}
false
```

La notation `Pointy{<:Real}` peut être utilisée pour exprimer l'analogue Julia d'un type *covariant*, tandis que `Pointy{>:Int}` représente l'analogue d'un type *contravariant*, mais techniquement, ceux-ci représentent des *ensembles* de types (voir [UnionAll Types](@ref)).

```jldoctest pointytype
julia> Pointy{Float64} <: Pointy{<:Real}
true

julia> Pointy{Real} <: Pointy{>:Int}
true
```

Tout comme les types abstraits classiques servent à créer une hiérarchie utile de types sur des types concrets, les types abstraits paramétriques servent le même objectif en ce qui concerne les types composites paramétriques. Nous aurions, par exemple, pu déclarer `Point{T}` comme un sous-type de `Pointy{T}` comme suit :

```jldoctest pointytype
julia> struct Point{T} <: Pointy{T}
           x::T
           y::T
       end
```

Étant donné une telle déclaration, pour chaque choix de `T`, nous avons `Point{T}` comme un sous-type de `Pointy{T}` :

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Float64}
true

julia> Point{Real} <: Pointy{Real}
true

julia> Point{AbstractString} <: Pointy{AbstractString}
true
```

Cette relation est également invariante :

```jldoctest pointytype
julia> Point{Float64} <: Pointy{Real}
false

julia> Point{Float64} <: Pointy{<:Real}
true
```

Les types abstraits paramétriques comme `Pointy` servent à définir des structures de données ou des comportements qui peuvent être généralisés pour différents types de données. Dans le cas d'une implémentation de point qui ne nécessite qu'une seule coordonnée parce que le point se trouve sur la ligne diagonale *x = y*, cela permet de simplifier la représentation tout en maintenant la flexibilité d'utiliser le type abstrait pour d'autres implémentations.

```jldoctest pointytype
julia> struct DiagPoint{T} <: Pointy{T}
           x::T
       end
```

Maintenant, à la fois `Point{Float64}` et `DiagPoint{Float64}` sont des implémentations de l'abstraction `Pointy{Float64}`, et de même pour chaque autre choix possible de type `T`. Cela permet de programmer à une interface commune partagée par tous les objets `Pointy`, implémentée à la fois pour `Point` et `DiagPoint`. Cela ne peut cependant pas être pleinement démontré, jusqu'à ce que nous ayons introduit des méthodes et le dispatch dans la section suivante, [Methods](@ref).

Il existe des situations où il peut ne pas être logique que les paramètres de type varient librement sur tous les types possibles. Dans de telles situations, on peut contraindre la portée de `T` comme suit :

```jldoctest realpointytype
julia> abstract type Pointy{T<:Real} end
```

Avec une telle déclaration, il est acceptable d'utiliser tout type qui est un sous-type de [`Real`](@ref) à la place de `T`, mais pas des types qui ne sont pas des sous-types de `Real` :

```jldoctest realpointytype
julia> Pointy{Float64}
Pointy{Float64}

julia> Pointy{Real}
Pointy{Real}

julia> Pointy{AbstractString}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got Type{AbstractString}

julia> Pointy{1}
ERROR: TypeError: in Pointy, in T, expected T<:Real, got a value of type Int64
```

Les paramètres de type pour les types composites paramétriques peuvent être restreints de la même manière :

```julia
struct Point{T<:Real} <: Pointy{T}
    x::T
    y::T
end
```

Pour donner un exemple concret de la façon dont toute cette machinerie de types paramétriques peut être utile, voici la définition réelle du type immuable [`Rational`](@ref) de Julia (sauf que nous omettons le constructeur ici pour des raisons de simplicité), représentant un rapport exact d'entiers :

```julia
struct Rational{T<:Integer} <: Real
    num::T
    den::T
end
```

Il n'est logique de prendre des ratios de valeurs entières, donc le type de paramètre `T` est restreint à être un sous-type de [`Integer`](@ref), et un ratio d'entiers représente une valeur sur la ligne des nombres réels, donc tout [`Rational`](@ref) est une instance de l'abstraction [`Real`](@ref).

### Tuple Types

Les tuples sont une abstraction des arguments d'une fonction – sans la fonction elle-même. Les aspects saillants des arguments d'une fonction sont leur ordre et leurs types. Par conséquent, un type de tuple est similaire à un type immuable paramétré où chaque paramètre est le type d'un champ. Par exemple, un type de tuple à 2 éléments ressemble au type immuable suivant :

```julia
struct Tuple2{A,B}
    a::A
    b::B
end
```

Cependant, il y a trois différences clés :

  * Les types de tuples peuvent avoir un nombre quelconque de paramètres.
  * Les types de tuples sont *covariants* dans leurs paramètres : `Tuple{Int}` est un sous-type de `Tuple{Any}`. Par conséquent, `Tuple{Any}` est considéré comme un type abstrait, et les types de tuples ne sont concrets que si leurs paramètres le sont.
  * Les tuples n'ont pas de noms de champ ; les champs ne sont accessibles que par index.

Les valeurs de tuple sont écrites avec des parenthèses et des virgules. Lorsqu'un tuple est construit, un type de tuple approprié est généré à la demande :

```jldoctest
julia> typeof((1,"foo",2.5))
Tuple{Int64, String, Float64}
```

Notez les implications de la covariance :

```jldoctest
julia> Tuple{Int,AbstractString} <: Tuple{Real,Any}
true

julia> Tuple{Int,AbstractString} <: Tuple{Real,Real}
false

julia> Tuple{Int,AbstractString} <: Tuple{Real,}
false
```

Intuitivement, cela correspond au fait que le type des arguments d'une fonction est un sous-type de la signature de la fonction (lorsque la signature correspond).

### Vararg Tuple Types

Le dernier paramètre d'un type de tuple peut être la valeur spéciale [`Vararg`](@ref), qui désigne n'importe quel nombre d'éléments supplémentaires :

```jldoctest
julia> mytupletype = Tuple{AbstractString,Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```

De plus, `Vararg{T}` correspond à zéro ou plusieurs éléments de type `T`. Les types de tuples Vararg sont utilisés pour représenter les arguments acceptés par les méthodes varargs (voir [Varargs Functions](@ref)).

La valeur spéciale `Vararg{T,N}` (lorsqu'elle est utilisée comme dernier paramètre d'un type de tuple) correspond exactement à `N` éléments de type `T`. `NTuple{N,T}` est un alias pratique pour `Tuple{Vararg{T,N}}`, c'est-à-dire un type de tuple contenant exactement `N` éléments de type `T`.

### Named Tuple Types

Les tuples nommés sont des instances du type [`NamedTuple`](@ref), qui a deux paramètres : un tuple de symboles donnant les noms des champs, et un type de tuple donnant les types des champs. Pour plus de commodité, les types `NamedTuple` sont imprimés à l'aide de la macro [`@NamedTuple`](@ref), qui fournit une syntaxe de type `struct` pratique pour déclarer ces types via des déclarations `key::Type`, où un `::Type` omis correspond à `::Any`.

```jldoctest
julia> typeof((a=1,b="hello")) # prints in macro form
@NamedTuple{a::Int64, b::String}

julia> NamedTuple{(:a, :b), Tuple{Int64, String}} # long form of the type
@NamedTuple{a::Int64, b::String}
```

La forme `begin ... end` du macro `@NamedTuple` permet de diviser les déclarations sur plusieurs lignes (similaire à une déclaration de struct), mais est autrement équivalente :

```jldoctest
julia> @NamedTuple begin
           a::Int
           b::String
       end
@NamedTuple{a::Int64, b::String}
```

Un type `NamedTuple` peut être utilisé comme constructeur, acceptant un seul argument tuple. Le type `NamedTuple` construit peut être soit un type concret, avec les deux paramètres spécifiés, soit un type qui spécifie uniquement les noms des champs :

```jldoctest
julia> @NamedTuple{a::Float32,b::String}((1, ""))
(a = 1.0f0, b = "")

julia> NamedTuple{(:a, :b)}((1, ""))
(a = 1, b = "")
```

Si les types de champ sont spécifiés, les arguments sont convertis. Sinon, les types des arguments sont utilisés directement.

### Parametric Primitive Types

Les types primitifs peuvent également être déclarés de manière paramétrique. Par exemple, les pointeurs sont représentés comme des types primitifs qui seraient déclarés en Julia comme ceci :

```julia
# 32-bit system:
primitive type Ptr{T} 32 end

# 64-bit system:
primitive type Ptr{T} 64 end
```

La caractéristique légèrement étrange de ces déclarations par rapport aux types composites paramétriques typiques est que le paramètre de type `T` n'est pas utilisé dans la définition du type lui-même – c'est juste une étiquette abstraite, définissant essentiellement toute une famille de types avec une structure identique, différenciée uniquement par leur paramètre de type. Ainsi, `Ptr{Float64}` et `Ptr{Int64}` sont des types distincts, même s'ils ont des représentations identiques. Et bien sûr, tous les types de pointeurs spécifiques sont des sous-types du type ombrelle [`Ptr`](@ref) :

```jldoctest
julia> Ptr{Float64} <: Ptr
true

julia> Ptr{Int64} <: Ptr
true
```

## UnionAll Types

Nous avons dit qu'un type paramétrique comme `Ptr` agit comme un supertype de toutes ses instances (`Ptr{Int64}` etc.). Comment cela fonctionne-t-il ? `Ptr` lui-même ne peut pas être un type de données normal, car sans connaître le type des données référencées, le type ne peut clairement pas être utilisé pour des opérations mémoire. La réponse est que `Ptr` (ou d'autres types paramétriques comme `Array`) est un type d'un autre genre appelé un type [`UnionAll`](@ref). Un tel type exprime l'*union itérée* de types pour toutes les valeurs d'un certain paramètre.

Les types `UnionAll` sont généralement écrits en utilisant le mot-clé `where`. Par exemple, `Ptr` pourrait être écrit plus précisément comme `Ptr{T} where T`, ce qui signifie toutes les valeurs dont le type est `Ptr{T}` pour une certaine valeur de `T`. Dans ce contexte, le paramètre `T` est également souvent appelé une "variable de type" car il ressemble à une variable qui varie selon les types. Chaque `where` introduit une seule variable de type, donc ces expressions sont imbriquées pour les types avec plusieurs paramètres, par exemple `Array{T,N} where N where T`.

La syntaxe d'application de type `A{B,C}` nécessite que `A` soit un type `UnionAll`, et substitue d'abord `B` pour la variable de type la plus externe dans `A`. Le résultat est censé être un autre type `UnionAll`, dans lequel `C` est ensuite substitué. Ainsi, `A{B,C}` est équivalent à `A{B}{C}`. Cela explique pourquoi il est possible d'instancier partiellement un type, comme dans `Array{Float64}` : la première valeur de paramètre a été fixée, mais la seconde varie encore sur toutes les valeurs possibles. En utilisant la syntaxe explicite `where`, n'importe quel sous-ensemble de paramètres peut être fixé. Par exemple, le type de tous les tableaux 1-dimensionnels peut être écrit comme `Array{T,1} where T`.

Les variables de type peuvent être restreintes par des relations de sous-type. `Array{T} where T<:Integer` fait référence à tous les tableaux dont le type d'élément est une sorte de [`Integer`](@ref). La syntaxe `Array{<:Integer}` est un raccourci pratique pour `Array{T} where T<:Integer`. Les variables de type peuvent avoir à la fois des bornes inférieures et supérieures. `Array{T} where Int<:T<:Number` fait référence à tous les tableaux de [`Number`](@ref)s qui peuvent contenir des `Int`s (puisque `T` doit être au moins aussi grand que `Int`). La syntaxe `where T>:Int` fonctionne également pour spécifier uniquement la borne inférieure d'une variable de type, et `Array{>:Int}` est équivalent à `Array{T} where T>:Int`.

Puisque les expressions `where` s'imbriquent, les bornes des variables de type peuvent faire référence aux variables de type extérieures. Par exemple, `Tuple{T,Array{S}} where S<:AbstractArray{T} where T<:Real` fait référence à des tuples de 2 éléments dont le premier élément est un [`Real`](@ref), et dont le deuxième élément est un `Array` de n'importe quel type de tableau dont le type d'élément contient le type du premier élément du tuple.

Le mot-clé `where` peut lui-même être imbriqué à l'intérieur d'une déclaration plus complexe. Par exemple, considérons les deux types créés par les déclarations suivantes :

```jldoctest
julia> const T1 = Array{Array{T, 1} where T, 1}
Vector{Vector} (alias for Array{Array{T, 1} where T, 1})

julia> const T2 = Array{Array{T, 1}, 1} where T
Array{Vector{T}, 1} where T
```

Le type `T1` définit un tableau unidimensionnel de tableaux unidimensionnels ; chacun des tableaux intérieurs se compose d'objets du même type, mais ce type peut varier d'un tableau intérieur à l'autre. D'autre part, le type `T2` définit un tableau unidimensionnel de tableaux unidimensionnels dont tous les tableaux intérieurs doivent avoir le même type. Notez que `T2` est un type abstrait, par exemple, `Array{Array{Int,1},1} <: T2`, tandis que `T1` est un type concret. En conséquence, `T1` peut être construit avec un constructeur sans argument `a=T1()`, mais `T2` ne peut pas.

Il existe une syntaxe pratique pour nommer de tels types, similaire à la forme abrégée de la syntaxe de définition de fonction :

```julia
Vector{T} = Array{T, 1}
```

Ceci est équivalent à `const Vector = Array{T,1} where T`. Écrire `Vector{Float64}` est équivalent à écrire `Array{Float64,1}`, et le type générique `Vector` a comme instances tous les objets `Array` où le deuxième paramètre – le nombre de dimensions du tableau – est 1, peu importe quel est le type d'élément. Dans les langages où les types paramétriques doivent toujours être spécifiés en entier, cela n'est pas particulièrement utile, mais en Julia, cela permet d'écrire simplement `Vector` pour le type abstrait incluant tous les tableaux denses unidimensionnels de n'importe quel type d'élément.

## [Singleton types](@id man-singleton-types)

Les types composites immuables sans champs sont appelés *singletons*. Formellement, si

1. `T` est un type composite immuable (c'est-à-dire défini avec `struct`),
2. `a est T && b est T` implique `a === b`,

alors `T` est un type singleton.[^2] [`Base.issingletontype`](@ref) peut être utilisé pour vérifier si un type est un type singleton. [Abstract types](@ref man-abstract-types) ne peut pas être des types singleton par construction.

D'après la définition, il s'ensuit qu'il ne peut y avoir qu'une seule instance de tels types :

```jldoctest
julia> struct NoFields
       end

julia> NoFields() === NoFields()
true

julia> Base.issingletontype(NoFields)
true
```

La fonction [`===`](@ref) confirme que les instances construites de `NoFields` sont en réalité une seule et même instance.

Les types paramétriques peuvent être des types singleton lorsque la condition ci-dessus est remplie. Par exemple,

```jldoctest
julia> struct NoFieldsParam{T}
       end

julia> Base.issingletontype(NoFieldsParam) # Can't be a singleton type ...
false

julia> NoFieldsParam{Int}() isa NoFieldsParam # ... because it has ...
true

julia> NoFieldsParam{Bool}() isa NoFieldsParam # ... multiple instances.
true

julia> Base.issingletontype(NoFieldsParam{Int}) # Parametrized, it is a singleton.
true

julia> NoFieldsParam{Int}() === NoFieldsParam{Int}()
true
```

## Types of functions

Chaque fonction a son propre type, qui est un sous-type de `Function`.

```jldoctest foo41
julia> foo41(x) = x + 1
foo41 (generic function with 1 method)

julia> typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)
```

Notez comment `typeof(foo41)` s'imprime comme lui-même. C'est simplement une convention d'impression, car c'est un objet de première classe qui peut être utilisé comme n'importe quelle autre valeur :

```jldoctest foo41
julia> T = typeof(foo41)
typeof(foo41) (singleton type of function foo41, subtype of Function)

julia> T <: Function
true
```

Les types de fonctions définis au niveau supérieur sont des singletons. Lorsque cela est nécessaire, vous pouvez les comparer avec [`===`](@ref).

[Closures](@ref man-anonymous-functions) ont également leur propre type, qui est généralement imprimé avec des noms se terminant par `#<number>`. Les noms et types des fonctions définies à différents emplacements sont distincts, mais il n'est pas garanti qu'ils soient imprimés de la même manière d'une session à l'autre.

```jldoctest; filter = r"[0-9\.]+"
julia> typeof(x -> x + 1)
var"#9#10"
```

Les types de fermetures ne sont pas nécessairement des singletons.

```jldoctest
julia> addy(y) = x -> x + y
addy (generic function with 1 method)

julia> typeof(addy(1)) === typeof(addy(2))
true

julia> addy(1) === addy(2)
false

julia> Base.issingletontype(typeof(addy(1)))
false
```

## [`Type{T}` type selectors](@id man-typet-type)

Pour chaque type `T`, `Type{T}` est un type paramétrique abstrait dont la seule instance est l'objet `T`. Jusqu'à ce que nous discutions de [Parametric Methods](@ref) et [conversions](@ref conversion-and-promotion), il est difficile d'expliquer l'utilité de ce construct, mais en bref, cela permet de spécialiser le comportement des fonctions sur des types spécifiques en tant que *valeurs*. Cela est utile pour écrire des méthodes (en particulier paramétriques) dont le comportement dépend d'un type qui est donné comme un argument explicite plutôt que sous-entendu par le type de l'un de ses arguments.

Puisque la définition est un peu difficile à comprendre, examinons quelques exemples :

```jldoctest
julia> isa(Float64, Type{Float64})
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true

julia> isa(Float64, Type{Real})
false
```

En d'autres termes, [`isa(A, Type{B})`](@ref) est vrai si et seulement si `A` et `B` sont le même objet et que cet objet est un type.

En particulier, puisque les types paramétriques sont [invariant](@ref man-parametric-composite-types), nous avons

```jldoctest
julia> struct TypeParamExample{T}
           x::T
       end

julia> TypeParamExample isa Type{TypeParamExample}
true

julia> TypeParamExample{Int} isa Type{TypeParamExample}
false

julia> TypeParamExample{Int} isa Type{TypeParamExample{Int}}
true
```

Sans le paramètre, `Type` est simplement un type abstrait qui a tous les objets de type comme ses instances :

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type)
true
```

Tout objet qui n'est pas un type n'est pas une instance de `Type` :

```jldoctest
julia> isa(1, Type)
false

julia> isa("foo", Type)
false
```

Bien que `Type` fasse partie de la hiérarchie des types de Julia comme tout autre type paramétrique abstrait, il n'est pas couramment utilisé en dehors des signatures de méthode, sauf dans certains cas particuliers. Un autre cas d'utilisation important pour `Type` est le renforcement des types de champ qui, autrement, seraient capturés de manière moins précise, par exemple comme [`DataType`](@ref man-declared-types) dans l'exemple ci-dessous où le constructeur par défaut pourrait entraîner des problèmes de performance dans le code s'appuyant sur le type enveloppé précis (similairement à [abstract type parameters](@ref man-performance-abstract-container)).

```jldoctest
julia> struct WrapType{T}
       value::T
       end

julia> WrapType(Float64) # default constructor, note DataType
WrapType{DataType}(Float64)

julia> WrapType(::Type{T}) where T = WrapType{Type{T}}(T)
WrapType

julia> WrapType(Float64) # sharpened constructor, note more precise Type{Float64}
WrapType{Type{Float64}}(Float64)
```

## Type Aliases

Parfois, il est pratique d'introduire un nouveau nom pour un type déjà exprimable. Cela peut être fait avec une simple instruction d'affectation. Par exemple, `UInt` est un alias pour soit [`UInt32`](@ref) soit [`UInt64`](@ref) selon la taille des pointeurs sur le système :

```julia-repl
# 32-bit system:
julia> UInt
UInt32

# 64-bit system:
julia> UInt
UInt64
```

Cela est accompli via le code suivant dans `base/boot.jl` :

```julia
if Int === Int64
    const UInt = UInt64
else
    const UInt = UInt32
end
```

Bien sûr, cela dépend de ce à quoi `Int` est aliasé – mais cela est prédéfini pour être le type correct – soit [`Int32`](@ref) soit [`Int64`](@ref).

(Notez que contrairement à `Int`, `Float` n'existe pas en tant qu'alias de type pour une taille spécifique [`AbstractFloat`](@ref). Contrairement aux registres d'entiers, où la taille de `Int` reflète la taille d'un pointeur natif sur cette machine, les tailles des registres à virgule flottante sont spécifiées par la norme IEEE-754.)

Les alias de type peuvent être paramétrés :

```jldoctest
julia> const Family{T} = Set{T}
Set

julia> Family{Char} === Set{Char}
true
```

## Operations on Types

Puisque les types en Julia sont eux-mêmes des objets, des fonctions ordinaires peuvent opérer sur eux. Certaines fonctions qui sont particulièrement utiles pour travailler avec ou explorer les types ont déjà été introduites, comme l'opérateur `<:`, qui indique si son opérande de gauche est un sous-type de son opérande de droite.

La fonction [`isa`](@ref) teste si un objet est d'un type donné et retourne vrai ou faux :

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, AbstractFloat)
false
```

La fonction [`typeof`](@ref), déjà utilisée tout au long du manuel dans des exemples, retourne le type de son argument. Puisque, comme mentionné ci-dessus, les types sont des objets, ils ont également des types, et nous pouvons demander quels sont leurs types :

```jldoctest
julia> typeof(Rational{Int})
DataType

julia> typeof(Union{Real,String})
Union
```

Que se passe-t-il si nous répétons le processus ? Quel est le type d'un type d'un type ? Comme il se trouve, les types sont toutes des valeurs composites et ont donc toutes un type de `DataType` :

```jldoctest
julia> typeof(DataType)
DataType

julia> typeof(Union)
DataType
```

`DataType` est son propre type.

Une autre opération qui s'applique à certains types est [`supertype`](@ref), qui révèle le supertype d'un type. Seuls les types déclarés (`DataType`) ont des supertypes non ambigus :

```jldoctest
julia> supertype(Float64)
AbstractFloat

julia> supertype(Number)
Any

julia> supertype(AbstractString)
Any

julia> supertype(Any)
Any
```

Si vous appliquez [`supertype`](@ref) à d'autres objets de type (ou objets non typés), une [`MethodError`](@ref) est levée :

```jldoctest; filter = r"Closest candidates.*"s
julia> supertype(Union{Float64,Int64})
ERROR: MethodError: no method matching supertype(::Type{Union{Float64, Int64}})
The function `supertype` exists, but no method is defined for this combination of argument types.

Closest candidates are:
[...]
```

## [Custom pretty-printing](@id man-custom-pretty-printing)

Souvent, on souhaite personnaliser la façon dont les instances d'un type sont affichées. Cela se fait en surchargeant la fonction [`show`](@ref). Par exemple, supposons que nous définissions un type pour représenter des nombres complexes sous forme polaire :

```jldoctest polartype
julia> struct Polar{T<:Real} <: Number
           r::T
           Θ::T
       end

julia> Polar(r::Real,Θ::Real) = Polar(promote(r,Θ)...)
Polar
```

Ici, nous avons ajouté une fonction constructeur personnalisée afin qu'elle puisse prendre des arguments de différents types [`Real`](@ref) et les promouvoir à un type commun (voir [Constructors](@ref man-constructors) et [Conversion and Promotion](@ref conversion-and-promotion)). (Bien sûr, nous devrions également définir beaucoup d'autres méthodes pour le faire agir comme un [`Number`](@ref), par exemple `+`, `*`, `one`, `zero`, règles de promotion, etc.) Par défaut, les instances de ce type s'affichent de manière assez simple, avec des informations sur le nom du type et les valeurs des champs, par exemple `Polar{Float64}(3.0,4.0)`.

Si nous voulons qu'il s'affiche plutôt comme `3.0 * exp(4.0im)`, nous définirions la méthode suivante pour imprimer l'objet dans un objet de sortie donné `io` (représentant un fichier, un terminal, un tampon, etc. ; voir [Networking and Streams](@ref)) :

```jldoctest polartype
julia> Base.show(io::IO, z::Polar) = print(io, z.r, " * exp(", z.Θ, "im)")
```

Un contrôle plus précis de l'affichage des objets `Polar` est possible. En particulier, il arrive que l'on souhaite à la fois un format d'impression multi-lignes verbeux, utilisé pour afficher un seul objet dans le REPL et d'autres environnements interactifs, et également un format compact sur une seule ligne utilisé pour [`print`](@ref) ou pour afficher l'objet dans le cadre d'un autre objet (par exemple dans un tableau). Bien que par défaut la fonction `show(io, z)` soit appelée dans les deux cas, vous pouvez définir un format multi-lignes *différent* pour afficher un objet en surchargeant une forme à trois arguments de `show` qui prend le type MIME `text/plain` comme deuxième argument (voir [Multimedia I/O](@ref Multimedia-I/O)), par exemple :

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/plain", z::Polar{T}) where{T} =
           print(io, "Polar{$T} complex number:\n   ", z)
```

(Notez que `print(..., z)` ici appellera la méthode `show(io, z)` à 2 arguments.) Cela donne :

```jldoctest polartype
julia> Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> [Polar(3, 4.0), Polar(4.0,5.3)]
2-element Vector{Polar{Float64}}:
 3.0 * exp(4.0im)
 4.0 * exp(5.3im)
```

où la forme sur une seule ligne `show(io, z)` est toujours utilisée pour un tableau de valeurs `Polar`. Techniquement, le REPL appelle `display(z)` pour afficher le résultat de l'exécution d'une ligne, ce qui par défaut appelle `show(stdout, MIME("text/plain"), z)`, qui à son tour par défaut appelle `show(stdout, z)`, mais vous ne devez *pas* définir de nouvelles méthodes [`display`](@ref) à moins que vous ne définissiez un nouveau gestionnaire d'affichage multimédia (voir [Multimedia I/O](@ref Multimedia-I/O)).

De plus, vous pouvez également définir des méthodes `show` pour d'autres types MIME afin de permettre un affichage plus riche (HTML, images, etc.) des objets dans des environnements qui le supportent (par exemple, IJulia). Par exemple, nous pouvons définir un affichage HTML formaté des objets `Polar`, avec des exposants et des italiques, via :

```jldoctest polartype
julia> Base.show(io::IO, ::MIME"text/html", z::Polar{T}) where {T} =
           println(io, "<code>Polar{$T}</code> complex number: ",
                   z.r, " <i>e</i><sup>", z.Θ, " <i>i</i></sup>")
```

Un objet `Polar` s'affichera alors automatiquement en utilisant HTML dans un environnement qui prend en charge l'affichage HTML, mais vous pouvez appeler `show` manuellement pour obtenir une sortie HTML si vous le souhaitez :

```jldoctest polartype
julia> show(stdout, "text/html", Polar(3.0,4.0))
<code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup>
```

```@raw html
<p>An HTML renderer would display this as: <code>Polar{Float64}</code> complex number: 3.0 <i>e</i><sup>4.0 <i>i</i></sup></p>
```

En règle générale, la méthode `show` sur une seule ligne doit imprimer une expression Julia valide pour créer l'objet affiché. Lorsque cette méthode `show` contient des opérateurs infixes, tels que l'opérateur de multiplication (`*`) dans notre méthode `show` sur une seule ligne pour `Polar` ci-dessus, il se peut qu'elle ne soit pas analysée correctement lorsqu'elle est imprimée dans le cadre d'un autre objet. Pour voir cela, considérez l'objet d'expression (voir [Program representation](@ref)) qui prend le carré d'une instance spécifique de notre type `Polar` :

```jldoctest polartype
julia> a = Polar(3, 4.0)
Polar{Float64} complex number:
   3.0 * exp(4.0im)

julia> print(:($a^2))
3.0 * exp(4.0im) ^ 2
```

Parce que l'opérateur `^` a une priorité plus élevée que `*` (voir [Operator Precedence and Associativity](@ref)), cette sortie ne représente pas fidèlement l'expression `a ^ 2` qui devrait être égale à `(3.0 * exp(4.0im)) ^ 2`. Pour résoudre ce problème, nous devons créer une méthode personnalisée pour `Base.show_unquoted(io::IO, z::Polar, indent::Int, precedence::Int)`, qui est appelée en interne par l'objet d'expression lors de l'impression :

```jldoctest polartype
julia> function Base.show_unquoted(io::IO, z::Polar, ::Int, precedence::Int)
           if Base.operator_precedence(:*) <= precedence
               print(io, "(")
               show(io, z)
               print(io, ")")
           else
               show(io, z)
           end
       end

julia> :($a^2)
:((3.0 * exp(4.0im)) ^ 2)
```

La méthode définie ci-dessus ajoute des parenthèses autour de l'appel à `show` lorsque la priorité de l'opérateur appelant est supérieure ou égale à la priorité de la multiplication. Cette vérification permet aux expressions qui se analysent correctement sans les parenthèses (comme `:($a + 2)` et `:($a == 2)`) de les omettre lors de l'impression :

```jldoctest polartype
julia> :($a + 2)
:(3.0 * exp(4.0im) + 2)

julia> :($a == 2)
:(3.0 * exp(4.0im) == 2)
```

Dans certains cas, il est utile d'ajuster le comportement des méthodes `show` en fonction du contexte. Cela peut être réalisé via le type [`IOContext`](@ref), qui permet de passer des propriétés contextuelles avec un flux IO encapsulé. Par exemple, nous pouvons construire une représentation plus courte dans notre méthode `show` lorsque la propriété `:compact` est définie sur `true`, en revenant à la longue représentation si la propriété est `false` ou absente :

```jldoctest polartype
julia> function Base.show(io::IO, z::Polar)
           if get(io, :compact, false)::Bool
               print(io, z.r, "ℯ", z.Θ, "im")
           else
               print(io, z.r, " * exp(", z.Θ, "im)")
           end
       end
```

Cette nouvelle représentation compacte sera utilisée lorsque le flux IO passé est un objet `IOContext` avec la propriété `:compact` définie. En particulier, c'est le cas lors de l'impression de tableaux avec plusieurs colonnes (où l'espace horizontal est limité) :

```jldoctest polartype
julia> show(IOContext(stdout, :compact=>true), Polar(3, 4.0))
3.0ℯ4.0im

julia> [Polar(3, 4.0) Polar(4.0,5.3)]
1×2 Matrix{Polar{Float64}}:
 3.0ℯ4.0im  4.0ℯ5.3im
```

Voir la documentation [`IOContext`](@ref) pour une liste de propriétés courantes qui peuvent être utilisées pour ajuster l'impression.

## "Value types"

En Julia, vous ne pouvez pas dispatcher sur une *valeur* telle que `true` ou `false`. Cependant, vous pouvez dispatcher sur des types paramétriques, et Julia vous permet d'inclure des valeurs de "bits simples" (Types, Symboles, Entiers, nombres à virgule flottante, tuples, etc.) en tant que paramètres de type. Un exemple courant est le paramètre de dimensionnalité dans `Array{T,N}`, où `T` est un type (par exemple, [`Float64`](@ref)) mais `N` est simplement un `Int`.

Vous pouvez créer vos propres types personnalisés qui prennent des valeurs en tant que paramètres et les utiliser pour contrôler le dispatch de types personnalisés. À titre d'illustration de cette idée, introduisons le type paramétrique `Val{x}`, et son constructeur `Val(x) = Val{x}()`, qui sert de manière habituelle à exploiter cette technique pour les cas où vous n'avez pas besoin d'une hiérarchie plus élaborée.

[`Val`](@ref) est défini comme :

```jldoctest valtype
julia> struct Val{x}
       end

julia> Val(x) = Val{x}()
Val
```

Il n'y a pas plus à l'implémentation de `Val` que cela. Certaines fonctions de la bibliothèque standard de Julia acceptent des instances de `Val` comme arguments, et vous pouvez également l'utiliser pour écrire vos propres fonctions. Par exemple :

```jldoctest valtype
julia> firstlast(::Val{true}) = "First"
firstlast (generic function with 1 method)

julia> firstlast(::Val{false}) = "Last"
firstlast (generic function with 2 methods)

julia> firstlast(Val(true))
"First"

julia> firstlast(Val(false))
"Last"
```

Pour la cohérence à travers Julia, le site d'appel doit toujours passer une instance de `Val` plutôt que d'utiliser un type, c'est-à-dire utiliser `foo(Val(:bar))` plutôt que `foo(Val{:bar})`.

Il convient de noter qu'il est extrêmement facile de mal utiliser les types "valeur" paramétriques, y compris `Val` ; dans des cas défavorables, vous pouvez facilement finir par rendre les performances de votre code beaucoup *pires*. En particulier, vous ne voudriez jamais écrire de code réel comme illustré ci-dessus. Pour plus d'informations sur les utilisations appropriées (et inappropriées) de `Val`, veuillez lire [the more extensive discussion in the performance tips](@ref man-performance-value-type).

[^1]: "Small" is defined by the `max_union_splitting` configuration, which currently defaults to 4.

[^2]: A few popular languages have singleton types, including Haskell, Scala and Ruby.
