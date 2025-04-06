```
ssh_key_name() :: String
```

La fonction `ssh_key_name()` renvoie le nom de base des fichiers de clé que SSH doit utiliser lors de l'établissement d'une connexion. Il n'y a généralement aucune raison d'appeler cette fonction directement et les bibliothèques devraient généralement utiliser les fonctions `ssh_key_path` et `ssh_pub_key_path` pour obtenir des chemins complets. Si la variable d'environnement `SSH_KEY_NAME` est définie, cette fonction renvoie celle-ci ; sinon, elle renvoie `id_rsa` par défaut.
