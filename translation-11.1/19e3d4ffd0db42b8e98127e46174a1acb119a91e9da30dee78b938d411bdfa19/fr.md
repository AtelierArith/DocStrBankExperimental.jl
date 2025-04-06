Le type `Header` est une structure représentant les métadonnées essentielles pour un seul enregistrement dans un fichier tar avec cette définition :

```
struct Header
    path :: String # chemin relatif à la racine
    type :: Symbol # indicateur de type (voir ci-dessous)
    mode :: UInt16 # mode/permissions (mieux visualisé en octal)
    size :: Int64  # taille des données de l'enregistrement en octets
    link :: String # chemin cible d'un lien symbolique
end
```

Les types sont représentés par les symboles suivants : `file`, `hardlink`, `symlink`, `chardev`, `blockdev`, `directory`, `fifo`, ou pour les types inconnus, le caractère typeflag en tant que symbole. Notez que [`extract`](@ref) refuse d'extraire des types d'enregistrements autres que `file`, `symlink` et `directory` ; [`list`](@ref) ne listera d'autres types d'enregistrements que si appelé avec `strict=false`.

Le format tar inclut diverses autres métadonnées sur les enregistrements, y compris les identifiants d'utilisateur et de groupe, les noms d'utilisateur et de groupe, et les horodatages. Le package `Tar`, par conception, ignore complètement ces champs. Lors de la création de fichiers tar, ces champs sont toujours définis sur zéro/vide. Lors de la lecture de fichiers tar, ces champs sont ignorés à l'exception de la vérification des sommes de contrôle des en-têtes pour chaque enregistrement d'en-tête pour tous les champs.
