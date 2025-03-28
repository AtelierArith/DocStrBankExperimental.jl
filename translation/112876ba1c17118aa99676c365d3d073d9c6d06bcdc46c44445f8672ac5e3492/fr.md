```
ssh_pub_key_path() :: String
```

La fonction `ssh_pub_key_path()` renvoie le chemin du fichier de clé publique SSH qui doit être utilisé pour les connexions SSH. Si la variable d'environnement `SSH_PUB_KEY_PATH` est définie, elle renverra cette valeur. Si cela n'est pas défini mais que `SSH_KEY_PATH` est défini, elle renverra ce chemin avec le suffixe `.pub` ajouté. Si aucun des deux n'est défini, elle renvoie par défaut

```
joinpath(ssh_dir(), ssh_key_name() * ".pub")
```

Cette valeur par défaut dépend à son tour des variables d'environnement `SSH_DIR` et `SSH_KEY_NAME`.
