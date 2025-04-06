```
find_library(noms [, emplacements])
```

Recherche la première bibliothèque dans `noms` dans les chemins de la liste `emplacements`, `DL_LOAD_PATH` ou les chemins de bibliothèque système (dans cet ordre) qui peut être dlopen'd avec succès. En cas de succès, la valeur de retour sera l'un des noms (potentiellement préfixé par l'un des chemins dans emplacements). Cette chaîne peut être assignée à un `global const` et utilisée comme nom de bibliothèque dans les futurs `ccall`. En cas d'échec, elle retourne la chaîne vide.
