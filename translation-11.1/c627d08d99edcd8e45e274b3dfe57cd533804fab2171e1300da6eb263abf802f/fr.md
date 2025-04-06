```
credential_callback(...) -> Cint
```

Une fonction de rappel d'identification LibGit2 qui fournit différentes fonctionnalités d'acquisition d'identifiants par rapport à un protocole de connexion. Le `payload_ptr` doit contenir un objet `LibGit2.CredentialPayload` qui suivra l'état et les paramètres.

Le `allowed_types` contient un masque de bits des valeurs `LibGit2.Consts.GIT_CREDTYPE` spécifiant quelles méthodes d'authentification doivent être tentées.

L'authentification des identifiants se fait dans l'ordre suivant (si pris en charge) :

  * Agent SSH
  * Paire de clés SSH privée/publique
  * Nom d'utilisateur/mot de passe en texte clair

Si un utilisateur se voit présenter une invite d'identification, il peut annuler l'invite en tapant `^D` (en appuyant sur la touche de contrôle avec la touche `d`).

**Remarque** : En raison des spécificités de la procédure d'authentification `libgit2`, lorsque l'authentification échoue, cette fonction est appelée à nouveau sans aucune indication si l'authentification a réussi ou non. Pour éviter une boucle infinie due à l'utilisation répétée des mêmes identifiants défectueux, nous suivrons l'état à l'aide du payload.

Pour plus de détails, consultez le guide LibGit2 sur [l'authentification contre un serveur](https://libgit2.org/docs/guides/authentication/).
