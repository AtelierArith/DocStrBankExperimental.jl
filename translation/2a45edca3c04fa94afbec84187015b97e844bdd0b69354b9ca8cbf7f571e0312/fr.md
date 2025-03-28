```
LibGit2.DescribeOptions
```

Correspond à la structure [`git_describe_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `max_candidates_tags` : considérer ce nombre de tags les plus récents dans `refs/tags` pour décrire un commit. Par défaut, 10 (de sorte que les 10 tags les plus récents soient examinés pour voir s'ils décrivent un commit).
  * `describe_strategy` : s'il faut considérer toutes les entrées dans `refs/tags` (équivalent à `git-describe --tags`) ou toutes les entrées dans `refs/` (équivalent à `git-describe --all`). La valeur par défaut est de n'afficher que les tags annotés. Si `Consts.DESCRIBE_TAGS` est passé, tous les tags, annotés ou non, seront considérés. Si `Consts.DESCRIBE_ALL` est passé, toute référence dans `refs/` sera considérée.
  * `pattern` : ne considérer que les tags qui correspondent à `pattern`. Prend en charge l'expansion glob.
  * `only_follow_first_parent` : lors de la recherche de la distance d'une référence correspondante à l'objet décrit, ne considérer que la distance par rapport au premier parent.
  * `show_commit_oid_as_fallback` : si aucune référence correspondante ne peut être trouvée pour décrire un commit, afficher le [`GitHash`](@ref) du commit au lieu de lancer une erreur (le comportement par défaut).
