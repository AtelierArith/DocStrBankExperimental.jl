# Using Valgrind with Julia

[Valgrind](https://valgrind.org/) est un outil pour le débogage de la mémoire, la détection des fuites de mémoire et le profilage. Cette section décrit les éléments à garder à l'esprit lors de l'utilisation de Valgrind pour déboguer des problèmes de mémoire avec Julia.

## General considerations

Par défaut, Valgrind suppose qu'il n'y a pas de code auto-modifiant dans les programmes qu'il exécute. Cette hypothèse fonctionne bien dans la plupart des cas, mais échoue misérablement pour un compilateur à la volée comme `julia`. Pour cette raison, il est crucial de passer `--smc-check=all-non-file` à `valgrind`, sinon le code peut planter ou se comporter de manière inattendue (souvent de manière subtile).

Dans certains cas, pour mieux détecter les erreurs de mémoire en utilisant Valgrind, il peut être utile de compiler `julia` avec les pools de mémoire désactivés. Le drapeau de compilation `MEMDEBUG` désactive les pools de mémoire dans Julia, et `MEMDEBUG2` désactive les pools de mémoire dans FemtoLisp. Pour construire `julia` avec les deux drapeaux, ajoutez la ligne suivante à `Make.user` :

```make
CFLAGS = -DMEMDEBUG -DMEMDEBUG2
```

Une autre chose à noter : si votre programme utilise plusieurs processus de travail, il est probable que vous souhaitiez que tous ces processus de travail s'exécutent sous Valgrind, et pas seulement le processus parent. Pour ce faire, passez `--trace-children=yes` à `valgrind`.

Encore une chose à noter : si vous utilisez `valgrind` et que vous obtenez des erreurs avec `Impossible de trouver une cible compatible dans l'image système`, essayez de reconstruire l'image système avec la cible `generic` ou de compiler julia avec `JULIA_CPU_TARGET=generic`.

## Suppressions

Valgrind affichera généralement des avertissements fallacieux pendant son exécution. Pour réduire le nombre de tels avertissements, il est utile de fournir un [suppressions file](https://valgrind.org/docs/manual/manual-core.html#manual-core.suppress) à Valgrind. Un fichier d'exemples de suppressions est inclus dans la distribution source de Julia à `contrib/valgrind-julia.supp`.

Le fichier de suppressions peut être utilisé depuis le répertoire source `julia/` comme suit :

```
$ valgrind --smc-check=all-non-file --suppressions=contrib/valgrind-julia.supp ./julia progname.jl
```

Toute erreur de mémoire affichée doit être signalée comme un bug ou contribué comme des suppressions supplémentaires. Notez que certaines versions de Valgrind sont [shipped with insufficient default suppressions](https://github.com/JuliaLang/julia/issues/8314#issuecomment-55766210), donc cela peut être une chose à considérer avant de soumettre des bugs.

## Running the Julia test suite under Valgrind

Il est possible d'exécuter l'ensemble de la suite de tests Julia sous Valgrind, mais cela prend beaucoup de temps (généralement plusieurs heures). Pour ce faire, exécutez la commande suivante depuis le répertoire `julia/test/` :

```
valgrind --smc-check=all-non-file --trace-children=yes --suppressions=$PWD/../contrib/valgrind-julia.supp ../julia runtests.jl all
```

Si vous souhaitez voir un rapport des fuites de mémoire "définitives", passez les options `--leak-check=full --show-leak-kinds=definite` à `valgrind` également.

## Additional spurious warnings

Cette section couvre les avertissements de Valgrind qui ne peuvent pas être ajoutés au fichier de suppressions mais qui sont néanmoins sûrs à ignorer.

### Unhandled rr system calls

Valgrind émettra un avertissement s'il rencontre l'un des [system calls that are specific to rr](https://github.com/rr-debugger/rr/blob/master/src/preload/rrcalls.h), le [Record and Replay Framework](https://rr-project.org/). En particulier, un avertissement concernant un syscall `1008` non géré sera affiché lorsque julia essaie de détecter si elle s'exécute sous rr :

```
--xxxxxx-- WARNING: unhandled amd64-linux syscall: 1008
--xxxxxx-- You may be able to write your own handler.
--xxxxxx-- Read the file README_MISSING_SYSCALL_OR_IOCTL.
--xxxxxx-- Nevertheless we consider this a bug.  Please report
--xxxxxx-- it at http://valgrind.org/support/bug_reports.html.
```

Ce problème [has been reported](https://bugs.kde.org/show_bug.cgi?id=446401) aux développeurs de Valgrind comme ils l'ont demandé.

## Caveats

Valgrind actuellement [does not support multiple rounding modes](https://bugs.kde.org/show_bug.cgi?id=136779), donc le code qui ajuste le mode d'arrondi se comportera différemment lorsqu'il sera exécuté sous Valgrind.

En général, si après avoir défini `--smc-check=all-non-file`, vous constatez que votre programme se comporte différemment lorsqu'il est exécuté sous Valgrind, il peut être utile de passer `--tool=none` à `valgrind` pendant que vous enquêtez davantage. Cela activera la machine minimale de Valgrind mais s'exécutera également beaucoup plus rapidement que lorsque le vérificateur de mémoire complet est activé.
