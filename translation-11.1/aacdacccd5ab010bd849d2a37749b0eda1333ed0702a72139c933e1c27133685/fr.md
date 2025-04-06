```
LibGit2.RebaseOperation
```

Décrit une seule instruction/opération à effectuer pendant le rebase. Correspond à la structure [`git_rebase_operation`](https://libgit2.org/libgit2/#HEAD/type/git_rebase_operation_t).

Les champs représentent :

  * `optype` : le type d'opération de rebase actuellement en cours. Les options sont :

      * `REBASE_OPERATION_PICK` : cherry-pick le commit en question.
      * `REBASE_OPERATION_REWORD` : cherry-pick le commit en question, mais réécrire son message en utilisant l'invite.
      * `REBASE_OPERATION_EDIT` : cherry-pick le commit en question, mais permettre à l'utilisateur de modifier le contenu du commit et son message.
      * `REBASE_OPERATION_SQUASH` : écraser le commit en question dans le commit précédent. Les messages de commit des deux commits seront fusionnés.
      * `REBASE_OPERATION_FIXUP` : écraser le commit en question dans le commit précédent. Seul le message de commit du commit précédent sera utilisé.
      * `REBASE_OPERATION_EXEC` : ne pas cherry-pick un commit. Exécuter une commande et continuer si la commande se termine avec succès.
  * `id` : le [`GitHash`](@ref) du commit sur lequel on travaille pendant cette étape de rebase.
  * `exec` : dans le cas où `REBASE_OPERATION_EXEC` est utilisé, la commande à exécuter pendant cette étape (par exemple, exécuter la suite de tests après chaque commit).
