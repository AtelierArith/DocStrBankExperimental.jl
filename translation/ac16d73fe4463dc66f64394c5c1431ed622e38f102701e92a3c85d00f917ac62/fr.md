# Running External Programs

Julia emprunte la notation de backtick pour les commandes du shell, Perl et Ruby. Cependant, en Julia, écrire

```jldoctest
julia> `echo hello`
`echo hello`
```

diffère à plusieurs égards du comportement dans divers shells, Perl ou Ruby :

  * Au lieu d'exécuter immédiatement la commande, les accents graves créent un objet [`Cmd`](@ref) pour représenter la commande. Vous pouvez utiliser cet objet pour connecter la commande à d'autres via des pipes, [`run`](@ref) cela, et [`read`](@ref) ou [`write`](@ref) à cela.
  * Lorsque la commande est exécutée, Julia ne capture pas sa sortie à moins que vous ne l'organisiez spécifiquement. Par défaut, la sortie de la commande va à [`stdout`](@ref) comme cela se ferait en utilisant l'appel `system` de `libc`.
  * La commande n'est jamais exécutée avec un shell. Au lieu de cela, Julia analyse directement la syntaxe de la commande, interpolant correctement les variables et séparant les mots comme le ferait le shell, en respectant la syntaxe de citation du shell. La commande est exécutée en tant que processus enfant immédiat de `julia`, en utilisant des appels `fork` et `exec`.

!!! note
    Le texte suivant suppose un environnement Posix comme sur Linux ou MacOS. Sur Windows, de nombreuses commandes similaires, telles que `echo` et `dir`, ne sont pas des programmes externes et sont plutôt intégrées dans le shell `cmd.exe` lui-même. Une option pour exécuter ces commandes est d'invoquer `cmd.exe`, par exemple `cmd /C echo hello`. Alternativement, Julia peut être exécutée dans un environnement Posix tel que Cygwin.


Voici un exemple simple d'exécution d'un programme externe :

```jldoctest
julia> mycommand = `echo hello`
`echo hello`

julia> typeof(mycommand)
Cmd

julia> run(mycommand);
hello
```

Le `hello` est la sortie de la commande `echo`, envoyée à [`stdout`](@ref). Si la commande externe échoue à s'exécuter correctement, la méthode run lance une [`ProcessFailedException`](@ref).

Si vous souhaitez lire la sortie de la commande externe, [`read`](@ref) ou [`readchomp`](@ref) peuvent être utilisés à la place :

```jldoctest
julia> read(`echo hello`, String)
"hello\n"

julia> readchomp(`echo hello`)
"hello"
```

Plus généralement, vous pouvez utiliser [`open`](@ref) pour lire ou écrire à partir d'une commande externe.

```jldoctest
julia> open(`less`, "w", stdout) do io
           for i = 1:3
               println(io, i)
           end
       end
1
2
3
```

Le nom du programme et les arguments individuels dans une commande peuvent être accédés et itérés comme si la commande était un tableau de chaînes :

```jldoctest
julia> collect(`echo "foo bar"`)
2-element Vector{String}:
 "echo"
 "foo bar"

julia> `echo "foo bar"`[2]
"foo bar"
```

## [Interpolation](@id command-interpolation)

Supposons que vous souhaitiez faire quelque chose d'un peu plus compliqué et utiliser le nom d'un fichier dans la variable `file` comme argument d'une commande. Vous pouvez utiliser `$` pour l'interpolation tout comme vous le feriez dans une chaîne littérale (voir [Strings](@ref)):

```jldoctest
julia> file = "/etc/passwd"
"/etc/passwd"

julia> `sort $file`
`sort /etc/passwd`
```

Un piège courant lors de l'exécution de programmes externes via un shell est que si un nom de fichier contient des caractères spéciaux pour le shell, cela peut entraîner un comportement indésirable. Supposons, par exemple, qu'au lieu de `/etc/passwd`, nous voulions trier le contenu du fichier `/Volumes/External HD/data.csv`. Essayons :

```jldoctest
julia> file = "/Volumes/External HD/data.csv"
"/Volumes/External HD/data.csv"

julia> `sort $file`
`sort '/Volumes/External HD/data.csv'`
```

Comment le nom de fichier a-t-il été cité ? Julia sait que `file` est censé être interpolé en tant qu'argument unique, donc elle cite le mot pour vous. En fait, ce n'est pas tout à fait exact : la valeur de `file` n'est jamais interprétée par un shell, donc il n'y a pas besoin de citation réelle ; les guillemets sont insérés uniquement pour la présentation à l'utilisateur. Cela fonctionnera même si vous interpolez une valeur dans le cadre d'un mot de shell :

```jldoctest
julia> path = "/Volumes/External HD"
"/Volumes/External HD"

julia> name = "data"
"data"

julia> ext = "csv"
"csv"

julia> `sort $path/$name.$ext`
`sort '/Volumes/External HD/data.csv'`
```

Comme vous pouvez le voir, l'espace dans la variable `path` est correctement échappé. Mais que faire si vous *voulez* interpoler plusieurs mots ? Dans ce cas, utilisez simplement un tableau (ou tout autre conteneur itérable) :

```jldoctest
julia> files = ["/etc/passwd","/Volumes/External HD/data.csv"]
2-element Vector{String}:
 "/etc/passwd"
 "/Volumes/External HD/data.csv"

julia> `grep foo $files`
`grep foo /etc/passwd '/Volumes/External HD/data.csv'`
```

Si vous interpolez un tableau dans le cadre d'un mot shell, Julia imite la génération d'arguments `{a,b,c}` du shell :

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> `grep xylophone $names.txt`
`grep xylophone foo.txt bar.txt baz.txt`
```

De plus, si vous interpolez plusieurs tableaux dans le même mot, le comportement de génération du produit cartésien du shell est émulé :

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> exts = ["aux","log"]
2-element Vector{String}:
 "aux"
 "log"

julia> `rm -f $names.$exts`
`rm -f foo.aux foo.log bar.aux bar.log baz.aux baz.log`
```

Puisque vous pouvez interpoler des tableaux littéraux, vous pouvez utiliser cette fonctionnalité générative sans avoir besoin de créer d'abord des objets de tableau temporaires :

```jldoctest
julia> `rm -rf $["foo","bar","baz","qux"].$["aux","log","pdf"]`
`rm -rf foo.aux foo.log foo.pdf bar.aux bar.log bar.pdf baz.aux baz.log baz.pdf qux.aux qux.log qux.pdf`
```

## Quoting

Inévitablement, on souhaite écrire des commandes qui ne sont pas si simples, et il devient nécessaire d'utiliser des guillemets. Voici un exemple simple d'une ligne Perl à un invite de commande :

```
sh$ perl -le '$|=1; for (0..3) { print }'
0
1
2
3
```

L'expression Perl doit être entre guillemets simples pour deux raisons : afin que les espaces ne divisent pas l'expression en plusieurs mots de shell, et afin que les utilisations des variables Perl comme `$|` (oui, c'est le nom d'une variable en Perl) ne provoquent pas d'interpolation. Dans d'autres cas, vous voudrez peut-être utiliser des guillemets doubles afin que l'interpolation *se produise* :

```
sh$ first="A"
sh$ second="B"
sh$ perl -le '$|=1; print for @ARGV' "1: $first" "2: $second"
1: A
2: B
```

En général, la syntaxe des backticks de Julia est soigneusement conçue pour que vous puissiez simplement couper et coller des commandes shell telles quelles dans des backticks et qu'elles fonctionnent : les comportements d'échappement, de citation et d'interpolation sont les mêmes que ceux du shell. La seule différence est que l'interpolation est intégrée et consciente de la notion de Julia de ce qui constitue une seule valeur de chaîne et ce qui est un conteneur pour plusieurs valeurs. Essayons les deux exemples ci-dessus dans Julia :

```jldoctest
julia> A = `perl -le '$|=1; for (0..3) { print }'`
`perl -le '$|=1; for (0..3) { print }'`

julia> run(A);
0
1
2
3

julia> first = "A"; second = "B";

julia> B = `perl -le 'print for @ARGV' "1: $first" "2: $second"`
`perl -le 'print for @ARGV' '1: A' '2: B'`

julia> run(B);
1: A
2: B
```

Les résultats sont identiques, et le comportement d'interpolation de Julia imite celui du shell avec quelques améliorations dues au fait que Julia prend en charge des objets itérables de première classe, tandis que la plupart des shells utilisent des chaînes de caractères séparées par des espaces pour cela, ce qui introduit des ambiguïtés. Lorsque vous essayez de porter des commandes shell vers Julia, essayez d'abord de couper et de coller. Étant donné que Julia vous montre les commandes avant de les exécuter, vous pouvez facilement et en toute sécurité examiner son interprétation sans causer de dommages.

## Pipelines

Les métacaractères de shell, tels que `|`, `&` et `>`, doivent être cités (ou échappés) à l'intérieur des backticks de Julia :

```jldoctest
julia> run(`echo hello '|' sort`);
hello | sort

julia> run(`echo hello \| sort`);
hello | sort
```

Cette expression invoque la commande `echo` avec trois mots comme arguments : `hello`, `|`, et `sort`. Le résultat est qu'une seule ligne est imprimée : `hello | sort`. Comment, alors, construit-on un pipeline ? Au lieu d'utiliser `'|'` à l'intérieur de backticks, on utilise [`pipeline`](@ref) :

```jldoctest
julia> run(pipeline(`echo hello`, `sort`));
hello
```

Cela envoie la sortie de la commande `echo` à la commande `sort`. Bien sûr, ce n'est pas très intéressant puisque qu'il n'y a qu'une seule ligne à trier, mais nous pouvons certainement faire des choses beaucoup plus intéressantes :

```julia-repl
julia> run(pipeline(`cut -d: -f3 /etc/passwd`, `sort -n`, `tail -n5`))
210
211
212
213
214
```

Cela imprime les cinq identifiants d'utilisateur les plus élevés sur un système UNIX. Les commandes `cut`, `sort` et `tail` sont toutes lancées en tant qu'enfants immédiats du processus `julia` actuel, sans processus shell intermédiaire. Julia elle-même effectue le travail de configuration des pipes et de connexion des descripteurs de fichiers qui est normalement effectué par le shell. Comme Julia fait cela elle-même, elle conserve un meilleur contrôle et peut faire certaines choses que les shells ne peuvent pas.

Julia peut exécuter plusieurs commandes en parallèle :

```jldoctest; filter = r"(world\nhello|hello\nworld)"
julia> run(`echo hello` & `echo world`);
world
hello
```

L'ordre de la sortie ici est non déterministe car les deux processus `echo` sont lancés presque simultanément et se disputent pour effectuer la première écriture dans le descripteur [`stdout`](@ref) qu'ils partagent avec l'autre et le processus parent `julia`. Julia vous permet de rediriger la sortie de ces deux processus vers un autre programme :

```jldoctest
julia> run(pipeline(`echo world` & `echo hello`, `sort`));
hello
world
```

En termes de plomberie UNIX, ce qui se passe ici est qu'un seul objet de pipe UNIX est créé et écrit par les deux processus `echo`, et l'autre extrémité du pipe est lue par la commande `sort`.

La redirection d'E/S peut être réalisée en passant des arguments clés `stdin`, `stdout` et `stderr` à la fonction `pipeline` :

```julia
pipeline(`do_work`, stdout=pipeline(`sort`, "out.txt"), stderr="errs.txt")
```

### Avoiding Deadlock in Pipelines

Lors de la lecture et de l'écriture aux deux extrémités d'un pipeline à partir d'un seul processus, il est important d'éviter de forcer le noyau à mettre en mémoire tampon toutes les données.

Par exemple, lors de la lecture de toute la sortie d'une commande, appelez `read(out, String)`, et non `wait(process)`, car le premier consommera activement toutes les données écrites par le processus, tandis que le second tentera de stocker les données dans les tampons du noyau en attendant qu'un lecteur soit connecté.

Une autre solution courante consiste à séparer le lecteur et l'écrivain du pipeline en deux [`Task`](@ref)s :

```julia
writer = @async write(process, "data")
reader = @async do_compute(read(process, String))
wait(writer)
fetch(reader)
```

(communiquement aussi, le lecteur n'est pas une tâche séparée, puisque nous le `fetch` immédiatement de toute façon).

### Complex Example

La combinaison d'un langage de programmation de haut niveau, d'une abstraction de commande de première classe et de la configuration automatique des canaux entre les processus est puissante. Pour donner une idée des pipelines complexes qui peuvent être créés facilement, voici quelques exemples plus sophistiqués, avec des excuses pour l'utilisation excessive de lignes de commande Perl :

```jldoctest prefixer; filter = r"([A-B] [0-5])"
julia> prefixer(prefix, sleep) = `perl -nle '$|=1; print "'$prefix' ", $_; sleep '$sleep';'`;

julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`, prefixer("A",2) & prefixer("B",2)));
B 0
A 1
B 2
A 3
B 4
A 5
```

Ceci est un exemple classique d'un producteur unique alimentant deux consommateurs concurrents : un processus `perl` génère des lignes avec les numéros de 0 à 5, tandis que deux processus parallèles consomment cette sortie, l'un préfixant les lignes avec la lettre "A", l'autre avec la lettre "B". Quel consommateur obtient la première ligne est non déterministe, mais une fois que cette course a été gagnée, les lignes sont consommées alternativement par un processus puis par l'autre. (Définir `$|=1` dans Perl fait en sorte que chaque instruction print vide le handle [`stdout`](@ref), ce qui est nécessaire pour que cet exemple fonctionne. Sinon, toute la sortie est mise en mémoire tampon et imprimée dans le tuyau d'un coup, pour être lue par un seul processus consommateur.)

Voici un exemple encore plus complexe de producteur-consommateur à plusieurs étapes :

```jldoctest prefixer; filter = r"[A-B] [X-Z] [0-5]"
julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`,
           prefixer("X",3) & prefixer("Y",3) & prefixer("Z",3),
           prefixer("A",2) & prefixer("B",2)));
A X 0
B Y 1
A Z 2
B X 3
A Y 4
B Z 5
```

Cet exemple est similaire au précédent, sauf qu'il y a deux étapes de consommateurs, et que les étapes ont des latences différentes, donc elles utilisent un nombre différent de travailleurs parallèles, pour maintenir un débit saturé.

Nous vous encourageons vivement à essayer tous ces exemples pour voir comment ils fonctionnent.

## `Cmd` Objects

La syntaxe des backticks crée un objet de type [`Cmd`](@ref). Un tel objet peut également être construit directement à partir d'un `Cmd` existant ou d'une liste d'arguments :

```julia
run(Cmd(`pwd`, dir=".."))
run(Cmd(["pwd"], detach=true, ignorestatus=true))
```

Cela vous permet de spécifier plusieurs aspects de l'environnement d'exécution de `Cmd` via des arguments de mot-clé. Par exemple, le mot-clé `dir` permet de contrôler le répertoire de travail de `Cmd` :

```jldoctest
julia> run(Cmd(`pwd`, dir="/"));
/
```

Et le mot-clé `env` vous permet de définir des variables d'environnement d'exécution :

```jldoctest
julia> run(Cmd(`sh -c "echo foo \$HOWLONG"`, env=("HOWLONG" => "ever!",)));
foo ever!
```

Voir [`Cmd`](@ref) pour des arguments de mot-clé supplémentaires. Les commandes [`setenv`](@ref) et [`addenv`](@ref) fournissent un autre moyen de remplacer ou d'ajouter aux variables d'environnement d'exécution de `Cmd`, respectivement :

```jldoctest
julia> run(setenv(`sh -c "echo foo \$HOWLONG"`, ("HOWLONG" => "ever!",)));
foo ever!

julia> run(addenv(`sh -c "echo foo \$HOWLONG"`, "HOWLONG" => "ever!"));
foo ever!
```
