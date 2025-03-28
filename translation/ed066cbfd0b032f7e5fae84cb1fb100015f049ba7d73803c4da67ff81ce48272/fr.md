```
ssh_key_path() :: String
```

La fonction `ssh_key_path()` renvoie le chemin du fichier de clé privée SSH qui doit être utilisé pour les connexions SSH. Si la variable d'environnement `SSH_KEY_PATH` est définie, elle renverra cette valeur. Sinon, elle renvoie par défaut

```
joinpath(ssh_dir(), ssh_key_name())
```

Cette valeur par défaut dépend à son tour des variables d'environnement `SSH_DIR` et `SSH_KEY_NAME`.
