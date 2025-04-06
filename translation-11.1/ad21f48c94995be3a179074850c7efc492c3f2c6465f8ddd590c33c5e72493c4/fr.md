```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Logging/docs/src/index.md"
```

# [Logging](@id man-logging)

Le module [`Logging`](@ref Logging.Logging) fournit un moyen d'enregistrer l'historique et le progrès d'un calcul sous forme de journal d'événements. Les événements sont créés en insérant une instruction de journalisation dans le code source, par exemple :

```julia
@warn "Abandon printf debugging, all ye who enter here!"
┌ Warning: Abandon printf debugging, all ye who enter here!
└ @ Main REPL[1]:1
```

Le système offre plusieurs avantages par rapport à l'insertion d'appels à `println()` dans votre code source. Tout d'abord, il vous permet de contrôler la visibilité et la présentation des messages sans modifier le code source. Par exemple, contrairement à l'`@warn` ci-dessus

```julia
@debug "The sum of some values $(sum(rand(100)))"
```

produira aucune sortie par défaut. De plus, il est très peu coûteux de laisser des instructions de débogage comme celle-ci dans le code source car le système évite d'évaluer le message s'il sera ensuite ignoré. Dans ce cas, `sum(rand(100))` et le traitement de chaîne associé ne seront jamais exécutés à moins que la journalisation de débogage ne soit activée.

Deuxièmement, les outils de journalisation vous permettent d'attacher des données arbitraires à chaque événement sous forme d'un ensemble de paires clé-valeur. Cela vous permet de capturer des variables locales et d'autres états du programme pour une analyse ultérieure. Par exemple, pour attacher la variable de tableau local `A` et la somme d'un vecteur `v` sous la clé `s`, vous pouvez utiliser

```jldoctest
A = ones(Int, 4, 4)
v = ones(100)
@info "Some variables"  A  s=sum(v)

# output
┌ Info: Some variables
│   A =
│    4×4 Matrix{Int64}:
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
└   s = 100.0
```

Tous les macros de journalisation `@debug`, `@info`, `@warn` et `@error` partagent des caractéristiques communes qui sont décrites en détail dans la documentation du macro plus général [`@logmsg`](@ref).

## Log event structure

Chaque événement génère plusieurs éléments de données, certains fournis par l'utilisateur et d'autres extraits automatiquement. Examinons d'abord les données définies par l'utilisateur :

  * Le *niveau de journalisation* est une catégorie large pour le message qui est utilisée pour un filtrage précoce. Il existe plusieurs niveaux standard de type [`LogLevel`](@ref) ; des niveaux définis par l'utilisateur sont également possibles. Chacun est distinct dans son objectif :

      * [`Logging.Debug`](@ref) (niveau de journal -1000) est une information destinée au développeur du programme. Ces événements sont désactivés par défaut.
      * [`Logging.Info`](@ref) (niveau de journal 0) est destiné à fournir des informations générales à l'utilisateur. Pensez-y comme une alternative à l'utilisation de `println` directement.
      * [`Logging.Warn`](@ref) (niveau de journal 1000) signifie que quelque chose ne va pas et qu'une action est probablement nécessaire, mais que pour l'instant le programme fonctionne toujours.
      * [`Logging.Error`](@ref) (niveau de journal 2000) signifie que quelque chose ne va pas et qu'il est peu probable que cela soit récupéré, du moins par cette partie du code. Souvent, ce niveau de journal est inutile car le lancement d'une exception peut transmettre toutes les informations requises.
  * Le *message* est un objet décrivant l'événement. Par convention, les `AbstractString` passés en tant que messages sont supposés être au format markdown. D'autres types seront affichés en utilisant `print(io, obj)` ou `string(obj)` pour une sortie textuelle et éventuellement `show(io,mime,obj)` pour d'autres affichages multimédias utilisés dans le journal installé.
  * Les *paires clé-valeur* optionnelles permettent d'attacher des données arbitraires à chaque événement. Certaines clés ont une signification conventionnelle qui peut affecter la façon dont un événement est interprété (voir [`@logmsg`](@ref)).

Le système génère également des informations standard pour chaque événement :

  * Le `module` dans lequel la macro de journalisation a été développée.
  * Le `fichier` et la `ligne` où la macro de journalisation se produit dans le code source.
  * Un identifiant `id` qui est un identifiant unique et fixe pour l'*instruction de code source* où la macro de journalisation apparaît. Cet identifiant est conçu pour être assez stable même si le code source du fichier change, tant que l'instruction de journalisation elle-même reste la même.
  * Un `groupe` pour l'événement, qui est défini par défaut sur le nom de base du fichier, sans extension. Cela peut être utilisé pour regrouper les messages en catégories plus fines que le niveau de journal (par exemple, tous les avertissements de dépréciation ont le groupe `:depwarn`), ou en regroupements logiques à travers ou au sein des modules.

Remarquez que certaines informations utiles, telles que l'heure de l'événement, ne sont pas incluses par défaut. Cela est dû au fait que ces informations peuvent être coûteuses à extraire et sont également *dynamiquement* disponibles pour le logger actuel. Il est simple de définir un [custom logger](@ref AbstractLogger-interface) pour compléter les données de l'événement avec l'heure, la trace de retour, les valeurs des variables globales et d'autres informations utiles selon les besoins.

## Processing log events

Comme vous pouvez le voir dans les exemples, les instructions de journalisation ne mentionnent pas où vont les événements de journal ou comment ils sont traités. C'est une caractéristique de conception clé qui rend le système composable et naturel pour une utilisation concurrente. Cela se fait en séparant deux préoccupations différentes :

  * *Créer* des événements de journal est la préoccupation de l'auteur du module qui doit décider où les événements sont déclenchés et quelles informations inclure.
  * *Traitement* des événements de journal — c'est-à-dire l'affichage, le filtrage, l'agrégation et l'enregistrement — est la préoccupation de l'auteur de l'application qui doit rassembler plusieurs modules dans une application coopérative.

### Loggers

Le traitement des événements est effectué par un *logger*, qui est le premier morceau de code configurable par l'utilisateur à voir l'événement. Tous les loggers doivent être des sous-types de [`AbstractLogger`](@ref).

Lorsque qu'un événement est déclenché, le logger approprié est trouvé en recherchant un logger local à la tâche avec le logger global comme solution de repli. L'idée ici est que le code de l'application sait comment les événements de journalisation doivent être traités et se trouve quelque part en haut de la pile d'appels. Nous devrions donc remonter la pile d'appels pour découvrir le logger — c'est-à-dire que le logger devrait être *dynamiquement scoping*. (C'est un point de contraste avec les frameworks de journalisation où le logger est *lexicalement scoping* ; fourni explicitement par l'auteur du module ou en tant que simple variable globale. Dans un tel système, il est difficile de contrôler la journalisation tout en composant des fonctionnalités à partir de plusieurs modules.)

Le journal global peut être configuré avec [`global_logger`](@ref), et les journaux locaux de tâche sont contrôlés à l'aide de [`with_logger`](@ref). Les tâches nouvellement créées héritent du journal de la tâche parente.

Il existe trois types de journaux fournis par la bibliothèque.  [`ConsoleLogger`](@ref) est le journal par défaut que vous voyez lorsque vous démarrez le REPL.  Il affiche les événements dans un format texte lisible et essaie de donner un contrôle simple mais convivial sur le formatage et le filtrage.  [`NullLogger`](@ref) est un moyen pratique de supprimer tous les messages si nécessaire ; c'est l'équivalent de journalisation du flux [`devnull`](@ref).  [`SimpleLogger`](@ref) est un journal de formatage texte très simpliste, principalement utile pour déboguer le système de journalisation lui-même.

Les enregistreurs personnalisés devraient être fournis avec des surcharges pour les fonctions décrites dans le [reference section](@ref AbstractLogger-interface).

### Early filtering and message handling

Lorsqu'un événement se produit, quelques étapes de filtrage précoce ont lieu pour éviter de générer des messages qui seront rejetés :

1. Le niveau de journalisation des messages est vérifié par rapport à un niveau minimum global (défini via [`disable_logging`](@ref)). C'est un paramètre global rudimentaire mais extrêmement économique.
2. L'état actuel du logger est consulté et le niveau de message est vérifié par rapport au niveau minimum mis en cache du logger, tel que trouvé en appelant [`Logging.min_enabled_level`](@ref). Ce comportement peut être remplacé via des variables d'environnement (plus d'informations à ce sujet plus tard).
3. La fonction [`Logging.shouldlog`](@ref) est appelée avec le logger actuel, prenant quelques informations minimales (niveau, module, groupe, id) qui peuvent être calculées statiquement. Plus utilement, `shouldlog` reçoit un `id` d'événement qui peut être utilisé pour rejeter les événements tôt en fonction d'un prédicat mis en cache.

Si tous ces contrôles passent, le message et les paires clé-valeur sont évalués dans leur intégralité et transmis au logger actuel via la fonction [`Logging.handle_message`](@ref). `handle_message()` peut effectuer un filtrage supplémentaire si nécessaire et afficher l'événement à l'écran, l'enregistrer dans un fichier, etc.

Les exceptions qui se produisent lors de la génération de l'événement de journal sont capturées et enregistrées par défaut. Cela empêche les événements individuels défectueux de faire planter l'application, ce qui est utile lors de l'activation d'événements de débogage peu utilisés dans un système de production. Ce comportement peut être personnalisé par type de logger en étendant [`Logging.catch_exceptions`](@ref).

## Testing log events

Log events are a side effect of running normal code, but you might find yourself wanting to test particular informational messages and warnings. The `Test` module provides a [`@test_logs`](@ref) macro that can be used to pattern match against the log event stream.

## Environment variables

Le filtrage des messages peut être influencé par la variable d'environnement [`JULIA_DEBUG`](@ref JULIA_DEBUG), et sert de moyen simple pour activer la journalisation de débogage pour un fichier ou un module. Charger julia avec `JULIA_DEBUG=loading` activera les messages de journalisation `@debug` dans `loading.jl`. Par exemple, dans les shells Linux :

```
$ JULIA_DEBUG=loading julia -e 'using OhMyREPL'
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
[ Info: Recompiling stale cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji for module OhMyREPL
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/Tokenize.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
...
```

Sur Windows, la même chose peut être réalisée dans `CMD` en exécutant d'abord `set JULIA_DEBUG="loading"` et dans `Powershell` via `$env:JULIA_DEBUG="loading"`.

De la même manière, la variable d'environnement peut être utilisée pour activer la journalisation de débogage des modules, tels que `Pkg`, ou des racines de module (voir [`Base.moduleroot`](@ref)). Pour activer toute la journalisation de débogage, utilisez la valeur spéciale `all`.

Pour activer la journalisation de débogage depuis le REPL, définissez `ENV["JULIA_DEBUG"]` sur le nom du module d'intérêt. Les fonctions définies dans le REPL appartiennent au module `Main` ; la journalisation pour celles-ci peut être activée comme ceci :

```julia-repl
julia> foo() = @debug "foo"
foo (generic function with 1 method)

julia> foo()

julia> ENV["JULIA_DEBUG"] = Main
Main

julia> foo()
┌ Debug: foo
└ @ Main REPL[1]:1

```

Utilisez un séparateur de virgule pour activer le débogage pour plusieurs modules : `JULIA_DEBUG=loading,Main`.

## Examples

### Example: Writing log events to a file

Parfois, il peut être utile d'écrire des événements de journal dans un fichier. Voici un exemple de la façon d'utiliser un journaliseur local à la tâche et un journaliseur global pour écrire des informations dans un fichier texte :

```julia-repl
# Load the logging module
julia> using Logging

# Open a textfile for writing
julia> io = open("log.txt", "w+")
IOStream(<file log.txt>)

# Create a simple logger
julia> logger = SimpleLogger(io)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# Log a task-specific message
julia> with_logger(logger) do
           @info("a context specific log message")
       end

# Write all buffered messages to the file
julia> flush(io)

# Set the global logger to logger
julia> global_logger(logger)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# This message will now also be written to the file
julia> @info("a global log message")

# Close the file
julia> close(io)
```

### Example: Enable debug-level messages

Voici un exemple de création d'un [`ConsoleLogger`](@ref) qui laisse passer tous les messages avec un niveau de journalisation supérieur ou égal à [`Logging.Debug`](@ref).

```julia-repl
julia> using Logging

# Create a ConsoleLogger that prints any log messages with level >= Debug to stderr
julia> debuglogger = ConsoleLogger(stderr, Logging.Debug)

# Enable debuglogger for a task
julia> with_logger(debuglogger) do
           @debug "a context specific log message"
       end

# Set the global logger
julia> global_logger(debuglogger)
```

## Reference

### Logging module

```@docs
Logging.Logging
```

### Creating events

```@docs
Logging.@logmsg
Logging.LogLevel
Logging.Debug
Logging.Info
Logging.Warn
Logging.Error
Logging.BelowMinLevel
Logging.AboveMaxLevel
```

### [Processing events with AbstractLogger](@id AbstractLogger-interface)

Le traitement des événements est contrôlé par la substitution des fonctions associées à `AbstractLogger` :

| Methods to implement                |                        | Brief description                            |
|:----------------------------------- |:---------------------- |:-------------------------------------------- |
| [`Logging.handle_message`](@ref)    |                        | Handle a log event                           |
| [`Logging.shouldlog`](@ref)         |                        | Early filtering of events                    |
| [`Logging.min_enabled_level`](@ref) |                        | Lower bound for log level of accepted events |
| **Optional methods**                | **Default definition** | **Brief description**                        |
| [`Logging.catch_exceptions`](@ref)  | `true`                 | Catch exceptions during event evaluation     |

```@docs
Logging.AbstractLogger
Logging.handle_message
Logging.shouldlog
Logging.min_enabled_level
Logging.catch_exceptions
Logging.disable_logging
```

### Using Loggers

Installation et inspection du logger :

```@docs
Logging.global_logger
Logging.with_logger
Logging.current_logger
```

Loggers fournis avec le système :

```@docs
Logging.NullLogger
Logging.ConsoleLogger
Logging.SimpleLogger
```
