```
create(
    [ prédicat, ] dir, [ tarball ];
    [ squelette, ] [ portable = false ]
) -> tarball

    prédicat :: String --> Bool
    dir       :: AbstractString
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    squelette  :: Union{AbstractString, AbstractCmd, IO}
    portable  :: Bool
```

Créez une archive tar ("tarball") du répertoire `dir`. L'archive résultante est écrite à l'emplacement `tarball` ou, si aucun emplacement n'est spécifié, un emplacement temporaire est créé et renvoyé par l'appel de fonction. Si `tarball` est un objet IO, alors le contenu du tarball est écrit dans ce handle à la place (le handle reste ouvert).

Si une fonction `prédicat` est passée, elle est appelée sur chaque chemin système rencontré lors de la recherche récursive dans `dir` et `path` n'est inclus dans le tarball que si `prédicat(path)` est vrai. Si `prédicat(path)` renvoie faux pour un répertoire, alors le répertoire est entièrement exclu : rien sous ce répertoire ne sera inclus dans l'archive.

Si le mot-clé `squelette` est passé, alors le fichier ou le handle IO donné est utilisé comme "squelette" pour générer le tarball. Vous créez un fichier squelette en passant le mot-clé `squelette` à la commande `extract`. Si `create` est appelé avec ce fichier squelette et que les fichiers extraits n'ont pas changé, un tarball identique est recréé. Les arguments `squelette` et `prédicat` ne peuvent pas être utilisés ensemble.

Si le drapeau `portable` est vrai, alors les noms de chemin sont vérifiés pour leur validité sur Windows, ce qui garantit qu'ils ne contiennent pas de caractères illégaux ou n'ont pas de noms réservés. Voir https://stackoverflow.com/a/31976060/659248 pour plus de détails.
