# Binary distributions

Ces notes sont destinées à ceux qui souhaitent compiler une distribution binaire de Julia pour distribution sur diverses plateformes. Nous aimons que les utilisateurs diffusent Julia aussi largement que possible, en l'essayant sur un large éventail de systèmes d'exploitation et de configurations matérielles. Comme chaque plateforme a des particularités et des processus spécifiques qui doivent être suivis pour créer une distribution Julia portable et fonctionnelle, nous avons séparé la plupart des notes par système d'exploitation.

Notez que bien que le code pour Julia soit [MIT-licensed, with a few exceptions](https://github.com/JuliaLang/julia/blob/master/LICENSE.md), la distribution créée par les techniques décrites ici sera sous licence GPL, car diverses bibliothèques dépendantes telles que `SuiteSparse` sont sous licence GPL. Nous espérons avoir une distribution non-GPL de Julia à l'avenir.

## Versioning and Git

Le Makefile utilise à la fois le fichier `VERSION` et les hachages de commit et les tags du dépôt git pour générer le fichier `base/version_git.jl` avec des informations que nous utilisons pour remplir l'écran de démarrage et la sortie de `versioninfo()`. Si pour une raison quelconque vous ne souhaitez pas avoir le dépôt git disponible lors de la construction, vous devez pré-générer le fichier `base/version_git.jl` avec :

```
make -C base version_git.jl.phony
```

Julia a beaucoup de dépendances de construction où nous utilisons des versions patchées qui n'ont pas encore été incluses par les gestionnaires de paquets populaires. Ces dépendances seront généralement téléchargées automatiquement lorsque vous construisez, mais si vous souhaitez pouvoir construire Julia sur un ordinateur sans accès à Internet, vous devez créer une archive full-source-dist avec la cible de make spéciale.

```
make full-source-dist
```

qui crée une archive julia-version-commit.tar.gz avec toutes les dépendances requises.

Lors de la compilation d'une version taguée dans le dépôt git, nous n'affichons pas les informations sur la branche/le hash de commit dans l'écran de démarrage. Vous pouvez utiliser cette ligne pour afficher une description de la version de jusqu'à 45 caractères. Pour définir cette ligne, vous devez créer un fichier Make.user contenant :

```
override TAGGED_RELEASE_BANNER = "my-package-repository build"
```

## Target Architectures

Par défaut, Julia optimise son image système pour l'architecture native de la machine de construction. Ce n'est généralement pas ce que vous souhaitez lors de la création de packages, car cela fera échouer Julia au démarrage sur toute machine avec des CPU incompatibles (en particulier les plus anciens avec des ensembles d'instructions plus restreints).

Nous vous recommandons donc de passer la variable `MARCH` lors de l'appel à `make`, en la définissant sur la cible de base que vous souhaitez prendre en charge. Cela déterminera le CPU cible pour l'exécutable Julia et les bibliothèques, ainsi que l'image système (cette dernière peut également être définie en utilisant [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET)). Les valeurs généralement utiles pour les CPU x86 sont `x86-64` et `core2` (pour les builds 64 bits) et `pentium4` (pour les builds 32 bits). Malheureusement, les CPU plus anciens que le Pentium 4 ne sont actuellement pas pris en charge (voir [this issue](https://github.com/JuliaLang/julia/issues/7185)).

La liste complète des cibles de CPU prises en charge par LLVM peut être obtenue en exécutant `llc -mattr=help`.

## Linux

Sur Linux, `make binary-dist` crée une archive tarball contenant une installation Julia entièrement fonctionnelle. Si vous souhaitez créer un paquet de distribution tel qu'un `.deb` ou un `.rpm`, un effort supplémentaire est nécessaire. Consultez le dépôt [julia-debian](https://github.com/staticfloat/julia-debian) pour un exemple de métadonnées nécessaires à la création de paquets `.deb` pour les systèmes basés sur Debian et Ubuntu. Consultez le [Fedora package](https://src.fedoraproject.org/rpms/julia) pour les distributions basées sur RPM. Bien que nous ne l'ayons pas encore expérimenté, [Alien](https://wiki.debian.org/Alien) pourrait être utilisé pour générer des paquets Julia pour diverses distributions Linux.

Julia prend en charge la substitution des répertoires d'installation standard via `prefix` et d'autres variables d'environnement que vous pouvez passer lors de l'appel de `make` et `make install`. Consultez Make.inc pour leur liste. `DESTDIR` peut également être utilisé pour forcer l'installation dans un répertoire temporaire.

Par défaut, Julia charge `$prefix/etc/julia/startup.jl` en tant que fichier d'initialisation à l'échelle de l'installation. Ce fichier peut être utilisé par les gestionnaires de distribution pour configurer des chemins ou du code d'initialisation personnalisés. Pour les paquets de distribution Linux, si `$prefix` est défini sur `/usr`, il n'y a pas de `/usr/etc` à examiner. Cela nécessite de changer le chemin vers le répertoire `etc` privé de Julia. Cela peut être fait via la variable de make `sysconfdir` lors de la construction. Il suffit de passer `sysconfdir=/etc` à `make` lors de la construction et Julia vérifiera d'abord `/etc/julia/startup.jl` avant d'essayer `$prefix/etc/julia/startup.jl`.

## OS X

Pour créer une distribution binaire sur OSX, construisez d'abord Julia, puis accédez à `contrib/mac/app`, et exécutez `make` avec les mêmes makevars qui ont été utilisés avec `make` lors de la construction de Julia proprement dite. Cela créera ensuite un fichier `.dmg` dans le répertoire `contrib/mac/app` contenant une application Julia.app complètement autonome.

Alternativement, Julia peut être construite en tant que framework en invoquant `make` avec la cible `darwinframework` et `DARWIN_FRAMEWORK=1` défini. Par exemple, `make DARWIN_FRAMEWORK=1 darwinframework`.

## Windows

Les instructions pour créer une distribution Julia sur Windows sont décrites dans le [build devdocs for Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md).

## Notes on BLAS and LAPACK

Julia construit OpenBLAS par défaut, ce qui inclut les bibliothèques BLAS et LAPACK. Sur les architectures 32 bits, Julia construit OpenBLAS pour utiliser des entiers 32 bits, tandis que sur les architectures 64 bits, Julia construit OpenBLAS pour utiliser des entiers 64 bits (ILP64). Il est essentiel que toutes les fonctions Julia qui appellent les routines API BLAS et LAPACK utilisent des entiers de la largeur correcte.

La plupart des distributions BLAS et LAPACK fournies sur les distributions linux, et même les implémentations commerciales, expédient des bibliothèques qui utilisent des API 32 bits. Dans de nombreux cas, une API 64 bits est fournie sous forme de bibliothèque séparée.

Lors de l'utilisation de bibliothèques fournies par le fournisseur ou par le système d'exploitation, une option `make` appelée `USE_BLAS64` est disponible dans le cadre de la construction de Julia. En exécutant `make USE_BLAS64=0`, Julia appellera BLAS et LAPACK en supposant une API 32 bits, où tous les entiers sont de 32 bits de large, même sur une architecture 64 bits.

D'autres bibliothèques que Julia utilise, comme SuiteSparse, utilisent également BLAS et LAPACK en interne. Les API doivent être cohérentes entre toutes les bibliothèques qui dépendent de BLAS et LAPACK. Le processus de construction de Julia construira toutes ces bibliothèques correctement, mais lorsqu'on remplace les valeurs par défaut et utilise des bibliothèques fournies par le système, cette cohérence doit être assurée.

Notez également que les distributions Linux expédient parfois plusieurs versions d'OpenBLAS, dont certaines activent le multithreading, tandis que d'autres ne fonctionnent qu'en mode série. Par exemple, dans Fedora, `libopenblasp.so` est multithreadé, mais `libopenblas.so` ne l'est pas. Nous recommandons d'utiliser le premier pour des performances optimales. Pour choisir une bibliothèque OpenBLAS dont le nom est différent de `libopenblas.so` par défaut, passez `LIBBLAS=-l$(YOURBLAS)` et `LIBBLASNAME=lib$(YOURBLAS)` à `make`, en remplaçant `$(YOURBLAS)` par le nom de votre bibliothèque. Vous pouvez également ajouter `.so.0` au nom de la bibliothèque si vous souhaitez que votre package fonctionne sans nécessiter le lien symbolique `.so` sans version.

Enfin, OpenBLAS inclut sa propre version optimisée de LAPACK. Si vous définissez `USE_SYSTEM_BLAS=1` et `USE_SYSTEM_LAPACK=1`, vous devez également définir `LIBLAPACK=-l$(YOURBLAS)` et `LIBLAPACKNAME=lib$(YOURBLAS)`. Sinon, la LAPACK de référence sera utilisée et les performances seront généralement beaucoup plus faibles.

À partir de Julia 1.7, Julia utilise [libblastrampoline](https://github.com/JuliaLinearAlgebra/libblastrampoline) pour choisir un BLAS différent à l'exécution.

# Point releasing 101

Créer une version de point/de correctif consiste en plusieurs étapes distinctes.

## Backporting commits

Certaines demandes de tirage sont étiquetées "backport pending x.y", par exemple "backport pending 0.6". Cela désigne que la prochaine version subséquente étiquetée à partir de la branche release-x.y devrait inclure le(s) commit(s) de cette demande de tirage. Une fois la demande de tirage fusionnée dans master, chacun des commits devrait être [cherry picked](https://git-scm.com/docs/git-cherry-pick) vers une branche dédiée qui sera finalement fusionnée dans release-x.y.

### Creating a backports branch

Tout d'abord, créez une nouvelle branche basée sur release-x.y. La convention typique pour les branches Julia est de préfixer le nom de la branche avec vos initiales si elle est destinée à être une branche personnelle. À titre d'exemple, nous dirons que l'auteur de la branche est Jane Smith.

```
git fetch origin
git checkout release-x.y
git rebase origin/release-x.y
git checkout -b js/backport-x.y
```

Cela garantit que votre copie locale de release-x.y est à jour avec l'origine avant de créer une nouvelle branche à partir de celle-ci.

### Cherry picking commits

Maintenant, nous faisons le véritable backporting. Trouvez toutes les pull requests fusionnées étiquetées "backport pending x.y" dans l'interface web de GitHub. Pour chacune d'elles, faites défiler jusqu'en bas où il est indiqué "someperson a fusionné le commit `123abc` dans `master` il y a XX minutes". Notez que le nom du commit est un lien ; si vous cliquez dessus, vous verrez le contenu du commit. Si cette page montre que `123abc` est un commit de fusion, retournez à la page de la PR - nous ne voulons pas de commits de fusion, nous voulons les commits réels. Cependant, si cela ne montre pas un commit de fusion, cela signifie que la PR a été fusionnée par squash. Dans ce cas, utilisez le SHA git du commit, indiqué à côté du commit sur cette page.

Une fois que vous avez le SHA du commit, appliquez-le sur la branche de rétroportage :

```
git cherry-pick -x -e <sha>
```

Il peut y avoir des conflits qui doivent être résolus manuellement. Une fois les conflits résolus (le cas échéant), ajoutez une référence à la demande de tirage GitHub qui a introduit le commit dans le corps du message de commit.

Après que tous les commits pertinents soient sur la branche de backports, poussez la branche sur GitHub.

## Checking for performance regressions

Les versions mineures ne devraient jamais introduire de régressions de performance. Heureusement, le bot de benchmarking Julia, Nanosoldier, peut exécuter des benchmarks contre n'importe quelle branche, pas seulement master. Dans ce cas, nous voulons vérifier les résultats des benchmarks de js/backport-x.y par rapport à release-x.y. Pour ce faire, réveillez le Nanosoldier de son sommeil robotique en utilisant un commentaire sur votre demande de tirage de backport :

```markdown
@nanosoldier `runbenchmarks(ALL, vs=":release-x.y")`
```

Cela exécutera tous les benchmarks enregistrés sur release-x.y et js/backport-x.y et produira un résumé des résultats, marquant toutes les améliorations et régressions.

Si Nanosoldier trouve des régressions, essayez de vérifier localement et de relancer Nanosoldier si nécessaire. Si les régressions sont jugées réelles plutôt que de simples bruits, vous devrez trouver un commit sur master à backporter qui le corrige si un existe, sinon vous devriez déterminer ce qui a causé la régression et soumettre un patch (ou demander à quelqu'un qui connaît le code de soumettre un patch) à master, puis backporter le commit une fois que cela a été fusionné. (Ou soumettre un patch directement à la branche de backport si approprié.)

## Building test binaries

Après que la PR de rétroportage a été fusionnée dans la branche `release-x.y`, mettez à jour votre clone local de Julia, puis obtenez le SHA de la branche en utilisant

```
git rev-parse origin/release-x.y
```

Gardez cela à portée de main, car c'est ce que vous entrerez dans le champ "Révision" de l'interface utilisateur de buildbot.

Pour l'instant, tout ce dont vous avez besoin ce sont des binaires pour Linux x86-64, car c'est ce qui est utilisé pour exécuter PackageEvaluator. Allez sur https://buildog.julialang.org, soumettez un travail pour `nuke_linux64`, puis mettez en file d'attente un travail pour `package_linux64`, en fournissant le SHA comme révision. Lorsque le travail de packaging est terminé, il téléchargera le binaire dans le bucket `julialang2` sur AWS. Récupérez l'URL, car elle sera utilisée pour PackageEvaluator.

## Checking for package breakages

Les versions mineures ne devraient jamais casser les paquets, à l'exception possible des paquets qui utilisent des hacks vraiment douteux en utilisant les internes de Base qui ne sont pas destinés à être visibles par l'utilisateur. (Dans ces cas, peut-être avoir une discussion avec l'auteur du paquet.)

Vérifier si les modifications apportées dans la prochaine nouvelle version vont casser des paquets peut être accompli en utilisant [PackageEvaluator](https://github.com/JuliaCI/PackageEvaluator.jl), souvent appelé "PkgEval" pour faire court. PkgEval est ce qui remplit les badges de statut sur les dépôts GitHub et sur pkg.julialang.org. Il s'exécute généralement sur l'un des nœuds non-benchmarking de Nanosoldier et utilise Vagrant pour effectuer ses tâches dans des machines virtuelles VirtualBox séparées et parallèles.

### Setting up PackageEvaluator

Clone PackageEvaluator et créez une branche appelée `backport-x.y.z`, puis vérifiez-la. Notez que les modifications requises sont un peu bricolées et déroutantes, et espérons que cela sera abordé dans une future version de PackageEvaluator. Les modifications à apporter seront modélisées sur [this commit](https://github.com/JuliaCI/PackageEvaluator.jl/commit/5ba6a3b000e7a3793391d16f695c8704b91d6016).

Le script de configuration prend son premier argument comme la version de Julia à exécuter et le second comme la plage de noms de packages (AK pour les packages nommés A-K, LZ pour L-Z). L'idée de base est que nous allons ajuster cela un peu pour exécuter uniquement deux versions de Julia, la version x.y actuelle et notre version de rétroportage, chacune avec trois plages de packages.

Dans le diff lié, nous disons que si le deuxième argument est LZ, utilisez les binaires construits à partir de notre branche de backport, sinon (AK) utilisez les binaires de la version. Ensuite, nous utilisons le premier argument pour exécuter une section de la liste des paquets : A-F pour l'entrée 0.4, G-N pour 0.5, et O-Z pour 0.6.

### Running PackageEvaluator

Pour exécuter PkgEval, trouvez une machine suffisamment puissante (comme le nœud 1 de Nanosoldier), puis exécutez

```
git clone https://github.com/JuliaCI/PackageEvaluator.jl.git
cd PackageEvaluator.jl/scripts
git checkout backport-x.y.z
./runvagrant.sh
```

Cela produit des dossiers dans le répertoire scripts/. Les noms des dossiers et leur contenu sont décodés ci-dessous :

| Folder name | Julia version | Package range |
|:-----------:|:-------------:|:-------------:|
|    0.4AK    |    Release    |      A-F      |
|    0.4LZ    |   Backport    |      A-F      |
|    0.5AK    |    Release    |      G-N      |
|    0.5LZ    |   Backport    |      G-N      |
|    0.6AK    |    Release    |      O-Z      |
|    0.6LZ    |   Backport    |      O-Z      |

### Investigating results

Une fois cela fait, vous pouvez utiliser `./summary.sh` depuis ce même répertoire pour produire un rapport de synthèse des résultats. Nous le ferons pour chacun des dossiers afin d'agréger les résultats globaux par version.

```
./summary.sh 0.4AK/*.json > summary_release.txt
./summary.sh 0.5AK/*.json >> summary_release.txt
./summary.sh 0.6AK/*.json >> summary_release.txt
./summary.sh 0.4LZ/*.json > summary_backport.txt
./summary.sh 0.5LZ/*.json >> summary_backport.txt
./summary.sh 0.6LZ/*.json >> summary_backport.txt
```

Maintenant, nous avons deux fichiers, `summary_release.txt` et `summary_backport.txt`, contenant les résultats des tests PackageEvaluator (réussite/échec) pour chaque package pour les deux versions.

Pour faciliter leur ingestion dans Julia, nous allons les convertir en fichiers CSV, puis utiliser le package DataFrames pour traiter les résultats. Pour convertir en CSV, copiez chaque fichier .txt dans un fichier .csv correspondant, puis entrez dans Vim et exécutez `ggVGI"<esc>` puis `:%s/\.json /",/g`. (Vous n'êtes pas obligé d'utiliser Vim ; c'est juste une façon de le faire.) Maintenant, traitez les résultats avec un code Julia similaire à ce qui suit.

```julia
using DataFrames

release = readtable("summary_release.csv", header=false, names=[:package, :release])
backport = readtable("summary_backport.csv", header=false, names=[:package, :backport])

results = join(release, backport, on=:package, kind=:outer)

for result in eachrow(results)
    a = result[:release]
    b = result[:backport]
    if (isna(a) && !isna(b)) || (isna(b) && !isna(a))
        color = :yellow
    elseif a != b && occursin("pass", b)
        color = :green
    elseif a != b
        color = :red
    else
        continue
    end
    printstyled(result[:package], ": Release ", a, " -> Backport ", b, "\n", color=color)
end
```

Cela écrira des lignes codées par couleur dans `stdout`. Toutes les lignes en rouge doivent être examinées car elles signifient des pannes potentielles causées par la version de backport. Les lignes en jaune doivent être vérifiées car cela signifie qu'un paquet a fonctionné sur une version mais pas sur l'autre pour une raison quelconque. Si vous constatez que votre branche de backport cause des pannes, utilisez `git bisect` pour identifier les commits problématiques, `git revert` ces commits, et répétez le processus.

## Merging backports into the release branch

Après vous être assuré que

  * les commits rétroportés passent tous les tests unitaires de Julia,
  * il n'y a pas de régressions de performance introduites par les commits rétroportés par rapport à la branche de publication, et
  * les commits rétroportés ne cassent aucun paquet enregistré,

alors la branche de backport est prête à être fusionnée dans release-x.y. Une fois fusionnée, passez en revue et retirez l'étiquette "backport pending x.y" de toutes les demandes de tirage contenant les commits qui ont été backportés. Ne retirez pas l'étiquette des PR qui n'ont pas été backportées.

La branche release-x.y devrait maintenant contenir tous les nouveaux commits. La dernière chose que nous voulons faire sur la branche est d'ajuster le numéro de version. Pour ce faire, soumettez une PR contre release-x.y qui modifie le fichier VERSION pour supprimer `-pre` du numéro de version. Une fois cela fusionné, nous sommes prêts à taguer.

## Tagging the release

C'est le moment ! Vérifiez la branche release-x.y et assurez-vous que votre copie locale de la branche est à jour avec la branche distante. À la ligne de commande, exécutez

```
git tag v$(cat VERSION)
git push --tags
```

Cela crée le tag localement et le pousse vers GitHub.

Après avoir tagué la version, soumettez une autre PR à release-x.y pour augmenter le numéro de patch et ajouter `-pre` à la fin. Cela indique que l'état de la branche reflète une version préliminaire de la prochaine version mineure de la série x.y.

Suivez les instructions restantes dans le Makefile.

## Signing binaries

Certaines de ces étapes nécessiteront des mots de passe sécurisés. Pour obtenir les mots de passe appropriés, contactez Elliot Saba (staticfloat) ou Alex Arslan (ararslan). Notez que la signature de code pour chaque plateforme doit être effectuée sur cette plateforme (par exemple, la signature Windows doit être faite sur Windows, etc.).

### Linux

La signature de code doit être effectuée manuellement sur Linux, mais c'est assez simple. Tout d'abord, obtenez le fichier `julia.key` dans le dossier CodeSigning du bucket AWS `juliasecure`. Ajoutez-le à votre trousseau de clés GnuPG en utilisant

```
gpg --import julia.key
```

Cela nécessitera d'entrer un mot de passe que vous devez obtenir d'Elliot ou d'Alex. Ensuite, définissez le niveau de confiance pour la clé au maximum. Commencez par entrer une session `gpg` :

```
gpg --edit-key julia
```

À l'invite, tapez `trust`, puis lorsque vous êtes invité à indiquer un niveau de confiance, fournissez le maximum disponible (probablement 5). Quittez GnuPG.

Maintenant, pour chacun des tarballs Linux qui ont été construits sur les buildbots, entrez

```
gpg -u julia --armor --detach-sig julia-x.y.z-linux-<arch>.tar.gz
```

Cela produira un fichier .asc correspondant pour chaque archive tar. Et c'est tout !

### macOS

La signature du code doit se faire automatiquement sur les buildbots macOS. Cependant, il est important de vérifier qu'elle a réussi. Sur un système ou une machine virtuelle exécutant macOS, téléchargez le fichier .dmg qui a été construit sur les buildbots. À titre d'exemple, disons que le fichier .dmg s'appelle `julia-x.y.z-osx.dmg`. Exécutez

```
mkdir ./jlmnt
hdiutil mount -readonly -mountpoint ./jlmnt julia-x.y.z-osx.dmg
codesign -v jlmnt/Julia-x.y.app
```

Assurez-vous de noter le nom du disque monté indiqué lors du montage ! À titre d'exemple, nous supposerons qu'il s'agit de `disk3`. Si la vérification de la signature de code s'est terminée avec succès, il n'y aura aucune sortie de l'étape `codesign`. Si cela a effectivement réussi, vous pouvez détacher le .dmg maintenant :

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
```

Si vous recevez un message comme

> Julia-x.y.app : l'objet de code n'est pas du tout signé


alors vous devrez signer manuellement.

Pour signer manuellement, récupérez d'abord les certificats OS X dans le dossier CodeSigning du bucket `juliasecure` sur AWS. Ajoutez le fichier .p12 à votre trousseau à l'aide de Keychain.app. Demandez à Elliot Saba (staticfloat) ou Alex Arslan (ararslan) le mot de passe pour la clé. Maintenant, exécutez

```
hdiutil convert julia-x.y.z-osx.dmg -format UDRW -o julia-x.y.z-osx_writable.dmg
mkdir ./jlmnt
hdiutil mount -mountpoint julia-x.y.z-osx_writable.dmg
codesign -s "AFB379C0B4CBD9DB9A762797FC2AB5460A2B0DBE" --deep jlmnt/Julia-x.y.app
```

Cela peut échouer avec un message comme

> Julia-x.y.app : le fork de ressources, les informations du Finder ou des débris similaires ne sont pas autorisés


Si c'est le cas, vous devrez supprimer les attributs superflus :

```
xattr -cr jlmnt/Julia-x.y.app
```

Ensuite, réessayez la signature du code. Si cela ne produit aucune erreur, réessayez la vérification. Si tout va bien maintenant, démontez le .dmg écrivable et convertissez-le à nouveau en lecture seule :

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
hdiutil convert julia-x.y.z-osx_writable.dmg -format UDZO -o julia-x.y.z-osx_fixed.dmg
```

Vérifiez que le .dmg résultant est en effet corrigé en double-cliquant dessus. Si tout semble bon, éjectez-le puis supprimez le suffixe `_fixed` du nom. Et c'est tout !

### Windows

La signature doit être effectuée manuellement sur Windows. Tout d'abord, obtenez le SDK Windows 10, qui contient les utilitaires de signature nécessaires, depuis le site Web de Microsoft. Nous avons besoin de l'utilitaire `SignTool` qui devrait avoir été installé quelque part comme `C:\Program Files (x86)\Windows Kits\10\App Certification Kit`. Récupérez les fichiers de certificat Windows depuis CodeSigning sur `juliasecure` et placez-les dans le même répertoire que les exécutables. Ouvrez une fenêtre CMD Windows, `cd` vers l'endroit où se trouvent tous les fichiers, et exécutez

```
set PATH=%PATH%;C:\Program Files (x86)\Windows Kits\10\App Certification Kit;
signtool sign /f julia-windows-code-sign_2017.p12 /p "PASSWORD" ^
   /t http://timestamp.verisign.com/scripts/timstamp.dll ^
   /v julia-x.y.z-win32.exe
```

Notez que `^` est un caractère de continuation de ligne dans Windows CMD et `PASSWORD` est un espace réservé pour le mot de passe de ce certificat. Comme d'habitude, contactez Elliot ou Alex pour les mots de passe. S'il n'y a pas d'erreurs, tout va bien !

## Uploading binaries

Maintenant que tout est signé, nous devons télécharger les binaires sur AWS. Vous pouvez utiliser un programme comme Cyberduck ou l'utilitaire en ligne de commande `aws`. Les binaires doivent aller dans le bucket `julialang2` dans les dossiers appropriés. Par exemple, Linux x86-64 va dans `julialang2/bin/linux/x.y`. Assurez-vous de supprimer le fichier actuel `julia-x.y-latest-linux-<arch>.tar.gz` et de le remplacer par un duplicata de `julia-x.y.z-linux-<arch>.tar.gz`.

Nous devons également télécharger les sommes de contrôle pour tout ce que nous avons construit, y compris les archives source et tous les binaires de version. C'est simple :

```
shasum -a 256 julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.sha256
md5sum julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.md5
```

Notez que si vous exécutez ces commandes sur macOS, vous obtiendrez une sortie légèrement différente, qui peut être reformattée en consultant un fichier existant. Les utilisateurs de Mac devront également utiliser `md5 -r` au lieu de `md5sum`. Téléchargez les fichiers .md5 et .sha256 dans `julialang2/bin/checksums` sur AWS.

Assurez-vous que les autorisations sur AWS pour tous les fichiers téléchargés sont définies sur "Tout le monde : LIRE."

Pour chaque fichier que nous avons téléchargé, nous devons purger le cache Fastly afin que les liens sur le site Web pointent vers les fichiers mis à jour. Par exemple :

```
curl -X PURGE https://julialang-s3.julialang.org/bin/checksums/julia-x.y.z.sha256
```

Parfois, ce n'est pas nécessaire, mais c'est bien de le faire quand même.
