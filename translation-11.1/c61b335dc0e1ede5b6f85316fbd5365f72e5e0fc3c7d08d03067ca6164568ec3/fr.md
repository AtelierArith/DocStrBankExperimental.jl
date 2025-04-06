```
stat(file)
```

Renvoie une structure dont les champs contiennent des informations sur le fichier. Les champs de la structure sont :

| Nom     | Type                            | Description                                                                             |
|:------- |:------------------------------- |:--------------------------------------------------------------------------------------- |
| desc    | `Union{String, Base.OS_HANDLE}` | Le chemin ou le descripteur de fichier OS                                               |
| size    | `Int64`                         | La taille (en octets) du fichier                                                        |
| device  | `UInt`                          | ID de l'appareil qui contient le fichier                                                |
| inode   | `UInt`                          | Le numéro d'inode du fichier                                                            |
| mode    | `UInt`                          | Le mode de protection du fichier                                                        |
| nlink   | `Int`                           | Le nombre de liens durs vers le fichier                                                 |
| uid     | `UInt`                          | L'identifiant de l'utilisateur du propriétaire du fichier                               |
| gid     | `UInt`                          | L'identifiant de groupe du propriétaire du fichier                                      |
| rdev    | `UInt`                          | Si ce fichier fait référence à un appareil, l'ID de l'appareil auquel il fait référence |
| blksize | `Int64`                         | La taille de bloc préférée par le système de fichiers pour le fichier                   |
| blocks  | `Int64`                         | Le nombre de blocs de 512 octets alloués                                                |
| mtime   | `Float64`                       | Horodatage Unix de la dernière modification du fichier                                  |
| ctime   | `Float64`                       | Horodatage Unix du dernier changement des métadonnées du fichier                        |
