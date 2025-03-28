# [Scoped Values](@id scoped-values)

Les valeurs scoping fournissent une implémentation du scoping dynamique en Julia.

!!! note "Lexical scoping vs dynamic scoping"
    [Lexical scoping](@ref scope-of-variables) est le comportement par défaut dans Julia. Sous le scoping lexical, la portée d'une variable est déterminée par la structure lexicale (textuelle) d'un programme. Sous le scoping dynamique, une variable est liée à la valeur assignée la plus récente pendant l'exécution du programme.


L'état d'une valeur scoping dépend du chemin d'exécution du programme. Cela signifie que pour une valeur scoping, vous pouvez observer plusieurs valeurs différentes simultanément.

!!! compat "Julia 1.11"
    Les valeurs scoping ont été introduites dans Julia 1.11. Dans Julia 1.8+, une implémentation compatible est disponible via le package ScopedValues.jl.


Dans sa forme la plus simple, vous pouvez créer un [`ScopedValue`](@ref Base.ScopedValues.ScopedValue) avec une valeur par défaut, puis utiliser [`with`](@ref Base.ScopedValues.with) ou [`@with`](@ref Base.ScopedValues.@with) pour entrer un nouveau scope dynamique. Le nouveau scope héritera de toutes les valeurs du scope parent (et récursivement de tous les scopes extérieurs) avec la valeur scoped fournie prenant la priorité sur les définitions précédentes.

Regardons d'abord un exemple de **portée** lexicale. Une instruction `let` commence une nouvelle portée lexicale dans laquelle la définition extérieure de `x` est masquée par sa définition intérieure.

```julia
x = 1
let x = 5
    @show x # 5
end
@show x # 1
```

Dans l'exemple suivant, puisque Julia utilise la portée lexicale, la variable `x` dans le corps de `f` fait référence à `x` défini dans la portée globale, et entrer dans une portée `let` ne change pas la valeur que `f` observe.

```julia
x = 1
f() = @show x
let x = 5
    f() # 1
end
f() # 1
```

Maintenant, en utilisant un `ScopedValue`, nous pouvons utiliser un **scoping** **dynamique**.

```julia
using Base.ScopedValues

x = ScopedValue(1)
f() = @show x[]
with(x=>5) do
    f() # 5
end
f() # 1
```

Notez que la valeur observée du `ScopedValue` dépend du chemin d'exécution du programme.

Il est souvent logique d'utiliser une variable `const` pour pointer vers une valeur de portée, et vous pouvez définir la valeur de plusieurs `ScopedValue` avec un seul appel à `with`.

```julia
using Base.ScopedValues

f() = @show a[]
g() = @show b[]

const a = ScopedValue(1)
const b = ScopedValue(2)

f() # a[] = 1
g() # b[] = 2

# Enter a new dynamic scope and set value.
with(a => 3) do
    f() # a[] = 3
    g() # b[] = 2
    with(a => 4, b => 5) do
        f() # a[] = 4
        g() # b[] = 5
    end
    f() # a[] = 3
    g() # b[] = 2
end

f() # a[] = 1
g() # b[] = 2
```

`ScopedValues` fournit une version macro de `with`. L'expression `@with var=>val expr` évalue `expr` dans un nouveau scope dynamique avec `var` défini sur `val`. `@with var=>val expr` est équivalent à `with(var=>val) do expr end`. Cependant, `with` nécessite une fermeture ou une fonction sans argument, ce qui entraîne un appel de cadre supplémentaire. Par exemple, considérons la fonction suivante `f` :

```julia
using Base.ScopedValues
const a = ScopedValue(1)
f(x) = a[] + x
```

Si vous souhaitez exécuter `f` dans un scope dynamique avec `a` défini sur `2`, vous pouvez utiliser `with` :

```julia
with(() -> f(10), a=>2)
```

Cependant, cela nécessite d'envelopper `f` dans une fonction sans argument. Si vous souhaitez éviter l'appel de cadre supplémentaire, vous pouvez utiliser le macro `@with` :

```julia
@with a=>2 f(10)
```

!!! note
    Les portées dynamiques sont héritées par [`Task`](@ref) au moment de la création de la tâche. Les portées dynamiques ne sont **pas** propagées à travers les opérations `Distributed.jl`.


Dans l'exemple ci-dessous, nous ouvrons un nouveau scope dynamique avant de lancer une tâche. La tâche parente et les deux tâches enfants observent des valeurs indépendantes de la même valeur scoped en même temps.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const scoped_val = ScopedValue(1)
@sync begin
    with(scoped_val => 2)
        @spawn @show scoped_val[] # 2
    end
    with(scoped_val => 3)
        @spawn @show scoped_val[] # 3
    end
    @show scoped_val[] # 1
end
```

Les valeurs de portée sont constantes tout au long d'une portée, mais vous pouvez stocker un état mutable dans une valeur de portée. Gardez simplement à l'esprit que les avertissements habituels concernant les variables globales s'appliquent dans le contexte de la programmation concurrente.

Des précautions sont également nécessaires lors du stockage de références à un état mutable dans des valeurs de portée. Vous voudrez peut-être explicitement [unshare mutable state](@ref unshare_mutable_state) lors de l'entrée dans une nouvelle portée dynamique.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# Example of using a mutable value wrongly
@sync begin
    # `Dict` is not thread-safe the usage below is invalid
    @spawn (sval_dict[][:a] = 3)
    @spawn (sval_dict[][:b] = 3)
end

@sync begin
    # If we instead pass a unique dictionary to each
    # task we can access the dictionaries race free.
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:a] = 3)
    end
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:b] = 3)
    end
end
```

## Example

Dans l'exemple ci-dessous, nous utilisons une valeur de portée pour implémenter un contrôle des permissions dans une application web. Après avoir déterminé les permissions de la requête, une nouvelle portée dynamique est entrée et la valeur de portée `LEVEL` est définie. D'autres parties de l'application peuvent interroger la valeur de portée et recevront la valeur appropriée. D'autres alternatives comme le stockage local de tâches et les variables globales ne conviennent pas bien à ce type de propagation ; notre seule alternative aurait été de transmettre une valeur à travers toute la chaîne d'appels.

```julia
using Base.ScopedValues

const LEVEL = ScopedValue(:GUEST)

function serve(request, response)
    level = isAdmin(request) ? :ADMIN : :GUEST
    with(LEVEL => level) do
        Threads.@spawn handle(request, response)
    end
end

function open(connection::Database)
    level = LEVEL[]
    if level !== :ADMIN
        error("Access disallowed")
    end
    # ... open connection
end

function handle(request, response)
    # ...
    open(Database(#=...=#))
    # ...
end
```

## Idioms

### [Unshare mutable state](@id unshare_mutable_state)

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# If you want to add new values to the dict, instead of replacing
# it, unshare the values explicitly. In this example we use `merge`
# to unshare the state of the dictionary in parent scope.
@sync begin
    with(sval_dict => merge(sval_dict[], Dict(:a => 10))) do
        @spawn @show sval_dict[][:a]
    end
    @spawn sval_dict[][:a] = 3 # Not a race since they are unshared.
end
```

### Scoped values as globals

Pour accéder à la valeur d'une valeur de portée, la valeur de portée elle-même doit être dans la portée (lexicale). Cela signifie que la plupart du temps, vous voudrez probablement utiliser des valeurs de portée comme des constantes globales.

```julia
using Base.ScopedValues
const sval = ScopedValue(1)
```

En effet, on peut penser aux valeurs de portée comme à des arguments de fonction cachés.

Cela n'exclut pas leur utilisation en tant que non-globaux.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

function main()
    role = ScopedValue(:client)

    function launch()
        #...
        role[]
    end

    @with role => :server @spawn launch()
    launch()
end
```

Mais il aurait peut-être été plus simple de passer directement l'argument de la fonction dans ces cas.

### Very many ScopedValues

Si vous vous retrouvez à créer de nombreux `ScopedValue` pour un module donné, il peut être préférable d'utiliser une structure dédiée pour les contenir.

```julia
using Base.ScopedValues

Base.@kwdef struct Configuration
    color::Bool = false
    verbose::Bool = false
end

const CONFIG = ScopedValue(Configuration(color=true))

@with CONFIG => Configuration(color=CONFIG[].color, verbose=true) begin
    @show CONFIG[].color # true
    @show CONFIG[].verbose # true
end
```

## API docs

```@docs
Base.ScopedValues.ScopedValue
Base.ScopedValues.with
Base.ScopedValues.@with
Base.isassigned(::Base.ScopedValues.ScopedValue)
Base.ScopedValues.get
```

## Implementation notes and performance

Les `Scope` utilisent un dictionnaire persistant. La recherche et l'insertion sont `O(log(32, n))`, lors de l'entrée dans un scope dynamique, une petite quantité de données est copiée et les données inchangées sont partagées entre d'autres scopes.

L'objet `Scope` lui-même n'est pas destiné aux utilisateurs et peut être modifié dans une future version de Julia.

## Design inspiration

This design was heavily inspired by [JEPS-429](https://openjdk.org/jeps/429), which in turn was inspired by dynamically scoped free variables in many Lisp dialects. In particular Interlisp-D and its deep binding strategy.

Un design précédent discuté était des variables de contexte comme [PEPS-567](https://peps.python.org/pep-0567/) et implémenté en Julia comme [ContextVariablesX.jl](https://github.com/tkf/ContextVariablesX.jl).
