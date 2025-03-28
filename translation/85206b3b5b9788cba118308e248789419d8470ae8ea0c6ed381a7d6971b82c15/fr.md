```
Downloader(; [ grace::Real = 30 ])
```

Les objets `Downloader` sont utilisés pour effectuer des opérations de `download` individuelles. Les connexions, les recherches de noms et d'autres ressources sont partagées au sein d'un `Downloader`. Ces connexions et ressources sont nettoyées après une période de grâce configurable (par défaut : 30 secondes) depuis la dernière opération de téléchargement effectuée avec celui-ci, ou lorsqu'il est collecté par le ramasse-miettes, selon la première éventualité. Si la période de grâce est fixée à zéro, toutes les ressources seront nettoyées immédiatement dès qu'il n'y a plus de téléchargements en cours. Si la période de grâce est fixée à `Inf`, alors les ressources ne seront pas nettoyées tant que le `Downloader` n'est pas collecté par le ramasse-miettes.
