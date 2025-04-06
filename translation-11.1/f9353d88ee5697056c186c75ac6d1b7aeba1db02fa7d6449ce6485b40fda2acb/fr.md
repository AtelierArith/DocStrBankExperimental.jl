```
rewrite(
    [ predicate, ] old_tarball, [ new_tarball ];
    [ portable = false, ]
) -> new_tarball

    predicate   :: Header --> Bool
    old_tarball :: Union{AbstractString, AbstractCmd, IO}
    new_tarball :: Union{AbstractString, AbstractCmd, IO}
    portable    :: Bool
```

Réécrit `old_tarball` au format standard que génère `create`, tout en vérifiant qu'il ne contient rien qui pourrait provoquer une erreur lors de l'extraction. Cela équivaut fonctionnellement à faire

```
Tar.create(Tar.extract(predicate, old_tarball), new_tarball)
```

Cependant, il n'extrait jamais rien sur le disque et utilise plutôt la fonction `seek` pour naviguer dans les données de l'ancien tarball. Si aucun argument `new_tarball` n'est passé, le nouveau tarball est écrit dans un fichier temporaire dont le chemin est retourné.

Si une fonction `predicate` est passée, elle est appelée sur chaque objet `Header` rencontré lors de l'extraction de `old_tarball` et l'entrée est ignorée à moins que `predicate(hdr)` ne soit vrai. Cela peut être utilisé pour réécrire sélectivement seulement certaines parties d'une archive, pour ignorer des entrées qui provoqueraient une erreur lors de l'extraction, ou pour enregistrer quel contenu est rencontré pendant le processus de réécriture.

Avant d'être passé à la fonction prédicat, l'objet `Header` est quelque peu modifié par rapport à l'en-tête brut dans le tarball : le champ `path` est normalisé pour supprimer les entrées `.` et remplacer plusieurs barres obliques consécutives par une seule barre oblique. Si l'entrée a le type `:hardlink`, le chemin de la cible du lien est normalisé de la même manière afin qu'il corresponde au chemin de l'entrée cible ; le champ de taille est défini sur la taille du chemin cible (qui doit être un fichier déjà vu).

Si le drapeau `portable` est vrai, alors les noms de chemin sont vérifiés pour leur validité sur Windows, ce qui garantit qu'ils ne contiennent pas de caractères illégaux ou n'ont pas de noms réservés. Voir https://stackoverflow.com/a/31976060/659248 pour plus de détails.
