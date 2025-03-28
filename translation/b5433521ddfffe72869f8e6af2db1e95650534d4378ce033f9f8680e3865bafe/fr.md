```
@debug message  [clé=valeur | valeur ...]
@info  message  [clé=valeur | valeur ...]
@warn  message  [clé=valeur | valeur ...]
@error message  [clé=valeur | valeur ...]

@logmsg niveau message [clé=valeur | valeur ...]

Créez un enregistrement de journal avec un `message` informatif. Pour plus de commodité, quatre macros de journalisation `@debug`, `@info`, `@warn` et `@error` sont définies, qui enregistrent aux niveaux de gravité standard `Debug`, `Info`, `Warn` et `Error`. `@logmsg` permet de définir `niveau` de manière programmatique à tout `LogLevel` ou types de niveaux de journal personnalisés.

`message` doit être une expression qui évalue à une chaîne qui est une description lisible par l'homme de l'événement de journal. Par convention, cette chaîne sera formatée en tant que markdown lorsqu'elle est présentée.

La liste optionnelle de paires `clé=valeur` prend en charge des métadonnées définies par l'utilisateur qui seront transmises au backend de journalisation dans le cadre de l'enregistrement de journal. Si seule une expression `valeur` est fournie, une clé représentant l'expression sera générée en utilisant [`Symbol`](@ref). Par exemple, `x` devient `x=x`, et `foo(10)` devient `Symbol("foo(10)")=foo(10)`. Pour splatter une liste de paires clé-valeur, utilisez la syntaxe de splatting normale, `@info "blah" kws...`.

Il existe certaines clés qui permettent de remplacer les données de journal générées automatiquement :

  * `_module=mod` peut être utilisé pour spécifier un module d'origine différent de l'emplacement source du message.
  * `_group=symbol` peut être utilisé pour remplacer le groupe de messages (cela est normalement dérivé du nom de base du fichier source).
  * `_id=symbol` peut être utilisé pour remplacer l'identifiant de message unique généré automatiquement. Cela est utile si vous devez associer très étroitement des messages générés sur différentes lignes de code source.
  * `_file=string` et `_line=integer` peuvent être utilisés pour remplacer l'emplacement source apparent d'un message de journal.

Il y a aussi quelques paires clé-valeur qui ont une signification conventionnelle :

  * `maxlog=integer` doit être utilisé comme un indice pour le backend que le message ne doit pas être affiché plus de `maxlog` fois.
  * `exception=ex` doit être utilisé pour transporter une exception avec un message de journal, souvent utilisé avec `@error`. Un backtrace associé `bt` peut être attaché en utilisant le tuple `exception=(ex,bt)`.

# Exemples

```

julia @debug "Informations de débogage détaillées. Invisible par défaut" @info  "Un message informatif" @warn  "Quelque chose était étrange. Vous devriez faire attention" @error "Une erreur non fatale s'est produite"

x = 10 @info "Certaines variables attachées au message" x a=42.0

@debug begin     sA = sum(A)     "sum(A) = :sA est une opération coûteuse, évaluée uniquement lorsque `shouldlog` renvoie vrai" end

for i=1:10000     @info "Avec le backend par défaut, vous ne verrez que (i = :i) dix fois"  maxlog=10     @debug "Algorithm1" i progress=i/10000 end ```
