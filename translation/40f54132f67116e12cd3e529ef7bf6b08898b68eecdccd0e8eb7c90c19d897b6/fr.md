```
print([io::IO = stdout,] [data::Vector = fetch()], [lidict::Union{LineInfoDict, LineInfoFlatDict} = getdict(data)]; kwargs...)
```

Imprime les résultats de profilage dans `io` (par défaut, `stdout`). Si vous ne fournissez pas de vecteur `data`, le tampon interne des backtraces accumulés sera utilisé.

Les arguments de mot-clé peuvent être n'importe quelle combinaison de :

  * `format` – Détermine si les backtraces sont imprimés avec (par défaut, `:tree`) ou sans (`:flat`) indentation indiquant la structure de l'arbre.
  * `C` – Si `true`, les backtraces du code C et Fortran sont affichés (normalement, ils sont exclus).
  * `combine` – Si `true` (par défaut), les pointeurs d'instruction sont fusionnés correspondant à la même ligne de code.
  * `maxdepth` – Limite la profondeur supérieure à `maxdepth` dans le format `:tree`.
  * `sortedby` – Contrôle l'ordre dans le format `:flat`. `:filefuncline` (par défaut) trie par la ligne source, `:count` trie par ordre du nombre d'échantillons collectés, et `:overhead` trie par le nombre d'échantillons encourus par chaque fonction elle-même.
  * `groupby` – Contrôle le regroupement sur les tâches et les threads, ou aucun regroupement. Les options sont `:none` (par défaut), `:thread`, `:task`, `[:thread, :task]`, ou `[:task, :thread]` où les deux dernières fournissent un regroupement imbriqué.
  * `noisefloor` – Limite les frames qui dépassent le seuil de bruit heuristique de l'échantillon (s'applique uniquement au format `:tree`). Une valeur suggérée à essayer pour cela est 2.0 (la valeur par défaut est 0). Ce paramètre cache les échantillons pour lesquels `n <= noisefloor * √N`, où `n` est le nombre d'échantillons sur cette ligne, et `N` est le nombre d'échantillons pour le callee.
  * `mincount` – Limite l'impression uniquement à ces lignes avec au moins `mincount` occurrences.
  * `recur` – Contrôle la gestion de la récursion dans le format `:tree`. `:off` (par défaut) imprime l'arbre normalement. `:flat` compresse à la place toute récursion (par ip), montrant l'effet approximatif de la conversion de toute auto-récursion en un itérateur. `:flatc` fait la même chose mais inclut également l'effondrement des frames C (peut faire des choses étranges autour de `jl_apply`).
  * `threads::Union{Int,AbstractVector{Int}}` – Spécifiez quels threads inclure des instantanés dans le rapport. Notez que cela ne contrôle pas quels threads les échantillons sont collectés (qui peuvent également avoir été collectés sur une autre machine).
  * `tasks::Union{Int,AbstractVector{Int}}` – Spécifiez quelles tâches inclure des instantanés dans le rapport. Notez que cela ne contrôle pas quelles tâches les échantillons sont collectés à l'intérieur.

!!! compat "Julia 1.8"
    Les arguments de mot-clé `groupby`, `threads`, et `tasks` ont été introduits dans Julia 1.8.


!!! note
    Le profilage sur Windows est limité au thread principal. D'autres threads n'ont pas été échantillonnés et ne figureront pas dans le rapport.

