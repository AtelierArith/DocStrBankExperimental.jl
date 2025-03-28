```
ssh_known_hosts_file() :: String
```

La fonction `ssh_known_hosts_file()` renvoie un seul chemin d'un fichier d'hôtes connus SSH qui doit être utilisé lors de l'établissement des identités des serveurs distants pour les connexions SSH. Elle renvoie le premier chemin retourné par `ssh_known_hosts_files` qui existe réellement. Les appelants qui peuvent consulter plus d'un fichier d'hôtes connus devraient utiliser `ssh_known_hosts_files` à la place et rechercher des correspondances d'hôtes dans tous les fichiers retournés comme décrit dans la documentation de cette fonction.
