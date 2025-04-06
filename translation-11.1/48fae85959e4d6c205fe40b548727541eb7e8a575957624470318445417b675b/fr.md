```
ssh_key_pass() :: String
```

La fonction `ssh_key_pass()` renvoie la valeur de la variable d'environnement `SSH_KEY_PASS` si elle est définie ou `nothing` si elle ne l'est pas. À l'avenir, il se peut qu'elle puisse trouver un mot de passe par d'autres moyens, tels que le stockage sécurisé du système, donc les packages qui ont besoin d'un mot de passe pour déchiffrer une clé privée SSH devraient utiliser cette API au lieu de vérifier directement la variable d'environnement afin de bénéficier automatiquement de telles capacités lorsqu'elles sont ajoutées.
