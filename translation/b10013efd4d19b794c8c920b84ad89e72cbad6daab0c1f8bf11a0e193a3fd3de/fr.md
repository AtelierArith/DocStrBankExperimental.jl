```
Cmd(cmd::Cmd; ignorestatus, detach, windows_verbatim, windows_hide, env, dir)
Cmd(exec::Vector{String})
```

Construit un nouvel objet `Cmd`, représentant un programme externe et des arguments, à partir de `cmd`, tout en modifiant les paramètres des arguments optionnels :

  * `ignorestatus::Bool` : Si `true` (par défaut `false`), alors le `Cmd` ne lancera pas d'erreur si le code de retour est non nul.
  * `detach::Bool` : Si `true` (par défaut `false`), alors le `Cmd` sera exécuté dans un nouveau groupe de processus, lui permettant de survivre au processus `julia` et de ne pas recevoir Ctrl-C.
  * `windows_verbatim::Bool` : Si `true` (par défaut `false`), alors sous Windows, le `Cmd` enverra une chaîne de commande au processus sans citation ni échappement des arguments, même pour les arguments contenant des espaces. (Sous Windows, les arguments sont envoyés à un programme sous forme d'une seule chaîne "de ligne de commande", et les programmes sont responsables de son analyse en arguments. Par défaut, les arguments vides et les arguments contenant des espaces ou des tabulations sont cités avec des guillemets doubles `"` dans la ligne de commande, et `\` ou `"` sont précédés de barres obliques inverses. `windows_verbatim=true` est utile pour lancer des programmes qui analysent leur ligne de commande de manière non standard.) N'a aucun effet sur les systèmes non-Windows.
  * `windows_hide::Bool` : Si `true` (par défaut `false`), alors sous Windows, aucune nouvelle fenêtre de console n'est affichée lorsque le `Cmd` est exécuté. Cela n'a aucun effet si une console est déjà ouverte ou sur des systèmes non-Windows.
  * `env` : Définit les variables d'environnement à utiliser lors de l'exécution du `Cmd`. `env` est soit un dictionnaire mappant des chaînes à des chaînes, un tableau de chaînes sous la forme `"var=val"`, un tableau ou un tuple de paires `"var"=>val`. Pour modifier (plutôt que remplacer) l'environnement existant, initialisez `env` avec `copy(ENV)` puis définissez `env["var"]=val` selon vos besoins. Pour ajouter à un bloc d'environnement dans un objet `Cmd` sans remplacer tous les éléments, utilisez [`addenv()`](@ref) qui renverra un objet `Cmd` avec l'environnement mis à jour.
  * `dir::AbstractString` : Spécifiez un répertoire de travail pour la commande (au lieu du répertoire actuel).

Pour tous les mots-clés qui ne sont pas spécifiés, les paramètres actuels de `cmd` sont utilisés.

Notez que le constructeur `Cmd(exec)` ne crée pas une copie de `exec`. Tout changement ultérieur de `exec` sera reflété dans l'objet `Cmd`.

La manière la plus courante de construire un objet `Cmd` est avec des littéraux de commande (backticks), par exemple :

```
`ls -l`
```

Cela peut ensuite être passé au constructeur `Cmd` pour modifier ses paramètres, par exemple :

```
Cmd(`echo "Hello world"`, ignorestatus=true, detach=false)
```
