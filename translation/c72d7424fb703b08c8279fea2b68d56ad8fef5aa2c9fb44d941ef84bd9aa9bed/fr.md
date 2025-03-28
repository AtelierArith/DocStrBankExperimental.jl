# macOS

Vous devez avoir les utilitaires de ligne de commande Xcode installés : exécutez `xcode-select --install` dans le terminal. Vous devrez réexécuter cette commande terminal après chaque mise à jour de macOS, sinon vous pourriez rencontrer des erreurs liées à des bibliothèques ou des en-têtes manquants.

Les bibliothèques dépendantes sont maintenant construites avec [BinaryBuilder](https://binarybuilder.org) et seront automatiquement téléchargées. C'est la méthode préférée pour construire le code source de Julia. Si vous souhaitez les construire toutes vous-même, vous aurez besoin d'un gfortran 64 bits pour compiler les dépendances de Julia.

```bash
brew install gcc
```

Si vous avez défini `LD_LIBRARY_PATH` ou `DYLD_LIBRARY_PATH` dans votre `.bashrc` ou équivalent, Julia peut ne pas être en mesure de trouver diverses bibliothèques qui l'accompagnent. Ces variables d'environnement doivent être désactivées pour que Julia fonctionne.
