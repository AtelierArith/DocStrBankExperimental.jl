```
ca_roots_path() :: String
```

La fonction `ca_roots_path()` est similaire à la fonction `ca_roots()` sauf qu'elle renvoie toujours un chemin vers un fichier ou un répertoire de racines d'autorité de certification encodées en PEM. Lorsqu'elle est appelée sur un système comme Windows ou macOS, où les certificats racines système ne sont pas stockés dans le système de fichiers, elle renverra actuellement le chemin vers l'ensemble des certificats racines qui sont fournis avec Julia. (À l'avenir, cette fonction pourrait plutôt extraire les certificats racines du système et les enregistrer dans un fichier dont le chemin serait renvoyé.)

S'il est possible de configurer une bibliothèque qui utilise TLS pour utiliser les certificats système, cela est généralement préférable : c'est-à-dire qu'il est mieux d'utiliser `ca_roots()` qui renvoie `nothing` pour indiquer que les certificats système doivent être utilisés. La fonction `ca_roots_path()` ne doit être utilisée que lors de la configuration de bibliothèques qui *exigent* un chemin vers un fichier ou un répertoire pour les certificats racines.

La valeur par défaut renvoyée par `ca_roots_path()` peut être remplacée en définissant les variables d'environnement `JULIA_SSL_CA_ROOTS_PATH`, `SSL_CERT_DIR` ou `SSL_CERT_FILE`, auquel cas cette fonction renverra toujours la valeur de la première de ces variables qui est définie (que le chemin existe ou non). Si `JULIA_SSL_CA_ROOTS_PATH` est défini sur une chaîne vide, alors les autres variables sont ignorées (comme si elles n'étaient pas définies) ; si les autres variables sont définies sur une chaîne vide, elles se comportent comme si elles n'étaient pas définies.
