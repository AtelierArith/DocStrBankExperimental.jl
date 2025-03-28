```
extract(
    [ prédicat, ] tarball, [ dir ];
    [ squelette = <aucun>, ]
    [ copier_liens_symboliques = <auto>, ]
    [ définir_permissions = true, ]
) -> dir

    prédicat        :: Header --> Bool
    tarball         :: Union{AbstractString, AbstractCmd, IO}
    dir             :: AbstractString
    squelette       :: Union{AbstractString, AbstractCmd, IO}
    copier_liens_symboliques :: Bool
    définir_permissions :: Bool
```

Extraire une archive tar ("tarball") située au chemin `tarball` dans le répertoire `dir`. Si `tarball` est un objet IO au lieu d'un chemin, alors le contenu de l'archive sera lu à partir de ce flux IO. L'archive est extraite dans `dir`, qui doit être soit un répertoire vide existant, soit un chemin inexistant qui peut être créé en tant que nouveau répertoire. Si `dir` n'est pas spécifié, l'archive est extraite dans un répertoire temporaire qui est renvoyé par `extract`.

Si une fonction `prédicat` est passée, elle est appelée sur chaque objet `Header` rencontré lors de l'extraction de `tarball` et l'entrée n'est extraite que si `prédicat(hdr)` est vrai. Cela peut être utilisé pour extraire sélectivement uniquement des parties d'une archive, pour ignorer des entrées qui provoquent une erreur lors de l'extraction, ou pour enregistrer ce qui est extrait pendant le processus d'extraction.

Avant d'être passée à la fonction prédicat, l'objet `Header` est quelque peu modifié par rapport à l'en-tête brut dans le tarball : le champ `path` est normalisé pour supprimer les entrées `.` et remplacer plusieurs barres obliques consécutives par une seule barre oblique. Si l'entrée a le type `:hardlink`, le chemin cible du lien est normalisé de la même manière afin qu'il corresponde au chemin de l'entrée cible ; le champ de taille est défini sur la taille du chemin cible (qui doit être un fichier déjà vu).

Si le mot-clé `squelette` est passé, alors un "squelette" du tarball extrait est écrit dans le fichier ou le handle IO donné. Ce fichier squelette peut être utilisé pour recréer un tarball identique en passant le mot-clé `squelette` à la fonction `create`. Les arguments `squelette` et `prédicat` ne peuvent pas être utilisés ensemble.

Si `copier_liens_symboliques` est `true`, alors au lieu d'extraire les liens symboliques tels quels, ils seront extraits comme des copies de ce à quoi ils se lient s'ils sont internes au tarball et si cela est possible. Les liens symboliques non internes, tels qu'un lien vers `/etc/passwd`, ne seront pas copiés. Les liens symboliques qui sont d'une manière ou d'une autre cycliques ne seront également pas copiés et seront plutôt ignorés. Par défaut, `extract` détectera si des liens symboliques peuvent être créés dans `dir` ou non et copiera automatiquement les liens symboliques s'ils ne peuvent pas être créés.

Si `définir_permissions` est `false`, aucune permission n'est définie sur les fichiers extraits.
