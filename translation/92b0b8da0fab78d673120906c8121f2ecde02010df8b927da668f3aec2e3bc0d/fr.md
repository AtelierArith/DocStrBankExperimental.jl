# Julia SSA-form IR

Julia utilise une représentation intermédiaire à affectation unique statique ([SSA IR](https://en.wikipedia.org/wiki/Static_single-assignment_form)) pour effectuer des optimisations. Cette IR est différente de l'IR LLVM et est unique à Julia. Elle permet des optimisations spécifiques à Julia.

1. Les blocs de base (régions sans flux de contrôle) sont explicitement annotés.
2. si/else et les boucles sont transformés en instructions `goto`.
3. les lignes avec plusieurs opérations sont divisées en plusieurs lignes en introduisant des variables.

Par exemple, le code Julia suivant :

```julia
function foo(x)
    y = sin(x)
    if x > 5.0
        y = y + cos(x)
    end
    return exp(2) + y
end
```

lorsqu'il est appelé avec un argument `Float64`, il est traduit en :

```julia
using InteractiveUtils
@code_typed foo(1.0)
```

```llvm
CodeInfo(
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
2 ─ %4 = invoke Main.cos(x::Float64)::Float64
└── %5 = Base.add_float(%1, %4)::Float64
3 ┄ %6 = φ (#2 => %5, #1 => %1)::Float64
│   %7 = Base.add_float(7.38905609893065, %6)::Float64
└──      return %7
) => Float64
```

Dans cet exemple, nous pouvons voir tous ces changements.

1. Le premier bloc de base est tout dans

```llvm
1 ─ %1 = invoke Main.sin(x::Float64)::Float64
│   %2 = Base.lt_float(x, 5.0)::Bool
└──      goto #3 if not %2
```

2. L'instruction `if` est traduite en `goto #3 if not %2` qui va au 3ème bloc de base si `x>5` n'est pas respecté et sinon va au deuxième bloc de base.
3. `%2` est une valeur SSA introduite pour représenter `x > 5`.

## Background

À partir de Julia 0.7, certaines parties du compilateur utilisent une nouvelle représentation intermédiaire (IR) [SSA-form](https://en.wikipedia.org/wiki/Static_single_assignment_form). Historiquement, le compilateur générait directement l'IR LLVM à partir d'une forme abaissée de l'AST Julia. Cette forme avait la plupart des abstractions syntaxiques supprimées, mais ressemblait encore beaucoup à un arbre de syntaxe abstraite. Au fil du temps, afin de faciliter les optimisations, des valeurs SSA ont été introduites dans cette IR et l'IR a été linéarisé (c'est-à-dire transformé en une forme où les arguments de fonction ne pouvaient être que des valeurs SSA ou des constantes). Cependant, des valeurs non-SSA (slots) sont restées dans l'IR en raison de l'absence de nœuds Phi dans l'IR (nécessaires pour les arêtes de retour et la re-fusion du flux de contrôle conditionnel). Cela a annulé une grande partie de l'utilité de la représentation en forme SSA lors de l'exécution des optimisations de milieu de gamme. Un effort héroïque a été déployé pour faire fonctionner ces optimisations sans une représentation complète en forme SSA, mais l'absence d'une telle représentation s'est finalement révélée prohibitive.

## Categories of IR nodes

La représentation IR SSA a quatre catégories de nœuds IR : nœuds Phi, Pi, PhiC et Upsilon (ces deux derniers ne sont utilisés que pour la gestion des exceptions).

### Phi nodes and Pi nodes

Les nœuds Phi font partie de l'abstraction SSA générique (voir le lien ci-dessus si vous n'êtes pas familier avec le concept). Dans l'IR de Julia, ces nœuds sont représentés comme :

```
struct PhiNode
    edges::Vector{Int32}
    values::Vector{Any}
end
```

où nous veillons à ce que les deux vecteurs aient toujours la même longueur. Dans la représentation canonique (celle gérée par codegen et l'interpréteur), les valeurs des arêtes indiquent les numéros des instructions d'origine (c'est-à-dire que si une arête a une entrée de `15`, il doit y avoir un `goto`, `gotoifnot` ou une chute implicite de l'instruction `15` qui cible ce nœud phi). Les valeurs sont soit des valeurs SSA, soit des constantes. Il est également possible qu'une valeur soit non assignée si la variable n'a pas été définie sur ce chemin. Cependant, les vérifications d'indéfinition sont explicitement insérées et représentées comme des booléens après les optimisations du milieu de l'exécution, donc les générateurs de code peuvent supposer que toute utilisation d'un nœud Phi aura une valeur assignée dans l'emplacement correspondant. Il est également légal que le mappage soit incomplet, c'est-à-dire qu'un nœud Phi ait des arêtes entrantes manquantes. Dans ce cas, il doit être garanti dynamiquement que la valeur correspondante ne sera pas utilisée.

Notez que SSA utilise sémantiquement "se produire après" le terminateur du prédécesseur correspondant ("sur le bord"). Par conséquent, si plusieurs nœuds Phi apparaissent au début d'un bloc de base, ils sont exécutés simultanément. Cela signifie que dans l'extrait IR suivant, si nous venons du bloc `23`, `%46` prendra la valeur associée à `%45` *avant* que nous entrions dans ce bloc.

```julia
%45 = φ (#18 => %23, #23 => %50)
%46 = φ (#18 => 1.0, #23 => %45)
```

PiNodes encode des informations prouvées statiquement qui peuvent être implicitement supposées dans des blocs de base dominés par un nœud pi donné. Ils sont conceptuellement équivalents à la technique introduite dans le document [ABCD: Eliminating Array Bounds Checks on Demand](https://dl.acm.org/citation.cfm?id=358438.349342) ou aux nœuds d'informations de prédicat dans LLVM. Pour voir comment ils fonctionnent, considérez, par exemple.

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    # use x
else
    # use x
end
```

Nous pouvons effectuer une insertion de prédicat et transformer cela en :

```julia
%x::Union{Int, Float64} # %x is some Union{Int, Float64} typed ssa value
if isa(x, Int)
    %x_int = PiNode(x, Int)
    # use %x_int
else
    %x_float = PiNode(x, Float64)
    # use %x_float
end
```

Les nœuds Pi sont généralement ignorés dans l'interpréteur, car ils n'ont aucun effet sur les valeurs, mais ils peuvent parfois conduire à la génération de code dans le compilateur (par exemple, pour passer d'une représentation de séparation d'union implicite à une représentation non emballée simple). L'utilité principale des nœuds Pi découle du fait que les conditions de chemin des valeurs peuvent être accumulées simplement en parcourant la chaîne de définition-utilisation qui est généralement effectuée pour la plupart des optimisations qui se soucient de ces conditions de toute façon.

### PhiC nodes and Upsilon nodes

La gestion des exceptions complique modérément l'histoire de la SSA, car la gestion des exceptions introduit des arêtes de flux de contrôle supplémentaires dans l'IR à travers lesquelles les valeurs doivent être suivies. Une approche pour y parvenir, suivie par LLVM, consiste à transformer les appels susceptibles de lancer des exceptions en terminators de blocs de base et à ajouter une arête de flux de contrôle explicite vers le gestionnaire d'exception :

```
invoke @function_that_may_throw() to label %regular unwind to %catch

regular:
# Control flow continues here

catch:
# Exceptions go here
```

Cependant, cela pose problème dans un langage comme Julia, où au début du pipeline d'optimisation, nous ne savons pas quelles appels peuvent lever des exceptions. Nous devrions supposer de manière conservatrice que chaque appel (qui, dans Julia, est chaque instruction) lève une exception. Cela aurait plusieurs effets négatifs. D'une part, cela réduirait essentiellement la portée de chaque bloc de base à un seul appel, ce qui annulerait l'objectif de faire exécuter des opérations au niveau du bloc de base. D'autre part, chaque bloc de base de capture aurait `n*m` arguments de nœud phi (`n`, le nombre d'instructions dans la région critique, `m` le nombre de valeurs actives à travers le bloc de capture).

Pour contourner cela, nous utilisons une combinaison de nœuds `Upsilon` et `PhiC` (le C signifiant `catch`, écrit `φᶜ` dans l'imprimante IR, car le sous-script unicode c n'est pas disponible). Il existe plusieurs façons de penser à ces nœuds, mais peut-être la plus simple est de considérer chaque `PhiC` comme un chargement à partir d'un emplacement unique de stockage-multiple, lu-une-fois, `Upsilon` étant l'opération de stockage correspondante. Le `PhiC` a une liste d'opérandes de tous les nœuds upsilon qui stockent dans son emplacement implicite. Les nœuds `Upsilon`, cependant, ne notent pas quel nœud `PhiC` ils stockent. Cela est fait pour une intégration plus naturelle avec le reste de l'IR SSA. Par exemple, s'il n'y a plus d'utilisations d'un nœud `PhiC`, il est sûr de le supprimer, et il en va de même pour un nœud `Upsilon`. Dans la plupart des passes IR, les nœuds `PhiC` peuvent être traités comme des nœuds `Phi`. On peut suivre les chaînes d'utilisation-définition à travers eux, et ils peuvent être élevés à de nouveaux nœuds `PhiC` et de nouveaux nœuds `Upsilon` (aux mêmes endroits que les nœuds `Upsilon` d'origine). Le résultat de ce schéma est que le nombre de nœuds `Upsilon` (et d'arguments `PhiC`) est proportionnel au nombre de valeurs assignées à une variable particulière (avant la conversion SSA), plutôt qu'au nombre d'instructions dans la région critique.

Pour voir ce schéma en action, considérez la fonction

```julia
@noinline opaque() = invokelatest(identity, nothing) # Something opaque
function foo()
    local y
    x = 1
    try
        y = 2
        opaque()
        y = 3
        error()
    catch
    end
    (x, y)
end
```

Le IR correspondant (avec les types non pertinents supprimés) est :

```
1 ─       nothing::Nothing
2 ─ %2  = $(Expr(:enter, #4))
3 ─ %3  = ϒ (false)
│   %4  = ϒ (#undef)
│   %5  = ϒ (1)
│   %6  = ϒ (true)
│   %7  = ϒ (2)
│         invoke Main.opaque()::Any
│   %9  = ϒ (true)
│   %10 = ϒ (3)
│         invoke Main.error()::Union{}
└──       $(Expr(:unreachable))::Union{}
4 ┄ %13 = φᶜ (%3, %6, %9)::Bool
│   %14 = φᶜ (%4, %7, %10)::Core.Compiler.MaybeUndef(Int64)
│   %15 = φᶜ (%5)::Core.Const(1)
└──       $(Expr(:leave, Core.SSAValue(2)))
5 ─       $(Expr(:pop_exception, :(%2)))::Any
│         $(Expr(:throw_undef_if_not, :y, :(%13)))::Any
│   %19 = Core.tuple(%15, %14)
└──       return %19
```

Notez en particulier que chaque valeur vivant dans la région critique obtient un nœud upsilon au sommet de la région critique. Cela est dû au fait que les blocs catch sont considérés comme ayant une arête de flux de contrôle invisible venant de l'extérieur de la fonction. En conséquence, aucune valeur SSA ne domine les blocs catch, et toutes les valeurs entrantes doivent passer par un nœud `φᶜ`.

## Main SSA data structure

La principale structure de données `SSAIR` mérite d'être discutée. Elle s'inspire de LLVM et de l'IR B3 de Webkit. Le cœur de la structure de données est un vecteur plat d'instructions. Chaque instruction se voit implicitement attribuer une valeur SSA en fonction de sa position dans le vecteur (c'est-à-dire que le résultat de l'instruction à l'index 1 peut être accédé en utilisant `SSAValue(1)`, etc.). Pour chaque valeur SSA, nous maintenons également son type. Étant donné que les valeurs SSA sont définies une seule fois, ce type est également le type de résultat de l'expression à l'index correspondant. Cependant, bien que cette représentation soit plutôt efficace (puisque les affectations n'ont pas besoin d'être explicitement codées), elle présente bien sûr l'inconvénient que l'ordre est sémantiquement significatif, donc les réordonnancements et les insertions changent les numéros d'instruction. De plus, nous ne conservons pas de listes d'utilisation (c'est-à-dire qu'il est impossible de passer d'une définition à toutes ses utilisations sans calculer explicitement cette carte - les listes de définitions cependant sont triviales puisque vous pouvez rechercher l'instruction correspondante à partir de l'index), donc l'opération RAUW (remplacer toutes les utilisations par) de style LLVM n'est pas disponible.

Au lieu de cela, nous faisons ce qui suit :

  * Nous maintenons un tampon séparé de nœuds à insérer (y compris la position à laquelle les insérer, le type de la valeur correspondante et le nœud lui-même). Ces nœuds sont numérotés par leur occurrence dans le tampon d'insertion, permettant à leurs valeurs d'être immédiatement utilisées ailleurs dans l'IR (c'est-à-dire que s'il y a 12 instructions dans la liste d'instructions originale, la première nouvelle instruction sera accessible sous la forme `SSAValue(13)`).
  * Les opérations de style RAUW sont effectuées en définissant l'index de déclaration correspondant à la valeur de remplacement.
  * Les déclarations sont effacées en définissant la déclaration correspondante à `rien` (c'est essentiellement juste une convention de cas spécial de ce qui précède).
  * S'il y a des utilisations de l'énoncé étant effacé, elles seront définies sur `rien`.

Il existe une fonction `compact!` qui compacte la structure de données ci-dessus en effectuant l'insertion de nœuds au bon endroit, la propagation de copies triviales et le renommage des utilisations vers les valeurs SSA modifiées. Cependant, la partie astucieuse de ce schéma est que cette compression peut être effectuée de manière paresseuse dans le cadre du passage suivant. La plupart des passes d'optimisation doivent parcourir l'ensemble de la liste des instructions, effectuant des analyses ou des modifications en cours de route. Nous fournissons un itérateur `IncrementalCompact` qui peut être utilisé pour itérer sur la liste des instructions. Il effectuera toute compression nécessaire et renverra le nouvel index du nœud, ainsi que le nœud lui-même. Il est légal à ce stade de parcourir les chaînes de définition-utilisation, ainsi que d'apporter des modifications ou des suppressions à l'IR (les insertions sont cependant interdites).

L'idée derrière cet agencement est que, puisque les passes d'optimisation doivent toucher la mémoire correspondante de toute façon et encourir la pénalité d'accès mémoire correspondante, effectuer les tâches supplémentaires de gestion devrait avoir un coût relativement faible (et économiser le coût de maintien de ces structures de données lors de la modification de l'IR).
