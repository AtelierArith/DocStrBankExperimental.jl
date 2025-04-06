```
mkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
mkpidlock(at::String, proc::Process; kwopts...)
```

Créez un verrou de fichier pid pour le chemin "at" pour le processus actuel ou le processus identifié par pid ou proc. Peut prendre une fonction à exécuter une fois verrouillé, pour une utilisation dans des blocs `do`, après quoi le verrou sera automatiquement fermé. Si le verrou échoue et que `wait` est faux, une erreur est levée.

Le verrou sera libéré soit par `close`, un `finalizer`, ou peu après la sortie de `proc`. Assurez-vous que la valeur de retour reste vivante jusqu'à la fin de la section critique de votre programme, afin que le `finalizer` ne la récupère pas trop tôt.

Arguments optionnels :

  * `mode` : mode d'accès au fichier (modifié par le umask du processus). Par défaut, il est lisible par tous.
  * `poll_interval` : Spécifiez le temps maximum entre les tentatives (si `watch_file` ne fonctionne pas)
  * `stale_age` : Supprimez un fichier pid existant (en ignorant le verrou) s'il est plus ancien que ce nombre de secondes, basé sur son mtime. Le fichier ne sera pas supprimé tant que 5 fois plus longtemps que cela si le pid dans le fichier semble valide. Ou 25 fois plus longtemps si `refresh` est remplacé par 0 pour désactiver le rafraîchissement du verrou. Par défaut, cela est désactivé (`stale_age` = 0), mais une valeur typiquement recommandée serait d'environ 3-5 fois un temps d'achèvement normal estimé.
  * `refresh` : Empêche un verrou de devenir obsolète en mettant à jour le mtime à chaque intervalle de temps qui passe. Par défaut, cela est réglé sur `stale_age/2`, qui est la valeur recommandée.
  * `wait` : Si vrai, bloque jusqu'à ce que nous obtenions le verrou, si faux, lève une erreur si le verrou échoue.
