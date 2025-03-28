```
LogRecord
```

Stocke les résultats d'un seul événement de journalisation. Champs :

  * `level` : le [`LogLevel`](@ref) du message de journalisation
  * `message` : le contenu textuel du message de journalisation
  * `_module` : le module de l'événement de journalisation
  * `group` : le groupe de journalisation (par défaut, le nom du fichier contenant l'événement de journalisation)
  * `id` : l'ID de l'événement de journalisation
  * `file` : le fichier contenant l'événement de journalisation
  * `line` : la ligne dans le fichier de l'événement de journalisation
  * `kwargs` : tous les arguments de mot-clé passés à l'événement de journalisation
