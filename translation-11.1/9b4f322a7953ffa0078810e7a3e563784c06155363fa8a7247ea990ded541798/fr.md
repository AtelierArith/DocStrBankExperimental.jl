# High-level Overview of the Native-Code Generation Process

## Representation of Pointers

Lors de l'émission de code vers un fichier objet, les pointeurs seront émis en tant que relocations. Le code de désérialisation veillera à ce que tout objet pointant vers l'une de ces constantes soit recréé et contienne le bon pointeur d'exécution.

Sinon, ils seront émis en tant que constantes littérales.

Pour émettre l'un de ces objets, appelez `literal_pointer_val`. Cela gérera le suivi de la valeur Julia et de l'global LLVM, en s'assurant qu'ils sont valides à la fois pour le runtime actuel et après désérialisation.

Lorsqu'ils sont émis dans le fichier objet, ces globaux sont stockés en tant que références dans une grande table `gvals`. Cela permet au désérialiseur de les référencer par index et d'implémenter un mécanisme manuel personnalisé similaire à une table de décalage global (GOT) pour les restaurer.

Les pointeurs de fonction sont gérés de manière similaire. Ils sont stockés en tant que valeurs dans une grande table `fvals`. Comme pour les variables globales, cela permet au désérialiseur de les référencer par index.

Notez que les fonctions `extern` sont traitées séparément, avec des noms, via le mécanisme habituel de résolution des symboles dans l'éditeur de liens.

Notez également que les fonctions `ccall` sont également gérées séparément, via une table de symboles (GOT) et une table de liaison de procédures (PLT) manuelles.

## Representation of Intermediate Values

Les valeurs sont transmises dans une structure `jl_cgval_t`. Cela représente une valeur R et inclut suffisamment d'informations pour déterminer comment l'assigner ou la passer quelque part.

Ils sont créés via l'un des constructeurs d'aide, généralement : `mark_julia_type` (pour les valeurs immédiates) et `mark_julia_slot` (pour les pointeurs vers des valeurs).

La fonction `convert_julia_type` peut transformer entre deux types quelconques. Elle renvoie une valeur R avec `cgval.typ` définie sur `typ`. Elle convertira l'objet dans la représentation demandée, en créant des boîtes sur le tas, en allouant des copies sur la pile et en calculant des unions étiquetées selon les besoins pour changer la représentation.

En revanche, `update_julia_type` changera `cgval.typ` en `typ`, uniquement si cela peut être fait à coût nul (c'est-à-dire sans émettre de code).

## Union representation

Les types d'union inférés peuvent être alloués sur la pile via une représentation de type tagué.

Les routines primitives qui doivent être capables de gérer des unions étiquetées sont :

  * type-de-marque
  * charger-local
  * store-local
  * isa
  * est
  * emit_typeof
  * emit_sizeof
  * encadré
  * déballer
  * spécialisé cc-ret

Tout le reste devrait pouvoir être géré lors de l'inférence en utilisant ces primitives pour mettre en œuvre la séparation des unions.

La représentation de l'union taguée est sous la forme d'une paire de `< void* union, byte sélecteur >`. Le sélecteur a une taille fixe de `byte & 0x7f`, et taguera l'union des 126 premiers isbits. Il enregistre le compte en profondeur basé sur un index un dans le type-union des objets isbits à l'intérieur. Un index de zéro indique que le `union*` est en réalité un `jl_value_t*` alloué sur le tas avec un tag, et doit être traité comme un objet normal pour un objet encapsulé plutôt que comme une union taguée.

Le bit élevé du sélecteur (`byte & 0x80`) peut être testé pour déterminer si le `void*` est en réalité une boîte allouée sur le tas (`jl_value_t*`), évitant ainsi le coût de la réallocation d'une boîte, tout en maintenant la capacité de gérer efficacement la séparation des unions en fonction des bits bas.

Il est garanti que `byte & 0x7f` est un test exact pour le type, si la valeur peut être représentée par un tag – elle ne sera jamais marquée `byte = 0x80`. Il n'est pas nécessaire de tester également le tag de type lors du test `isa`.

La région mémoire `union*` peut être allouée à *n'importe quelle* taille. La seule contrainte est qu'elle doit être suffisamment grande pour contenir les données actuellement spécifiées par `selector`. Elle pourrait ne pas être assez grande pour contenir l'union de tous les types qui pourraient y être stockés selon le champ de type Union associé. Utilisez une attention appropriée lors de la copie.

## Specialized Calling Convention Signature Representation

Un objet `jl_returninfo_t` décrit les détails de la convention d'appel de tout appelable.

Si l'un des arguments ou le type de retour d'une méthode peut être représenté sans boîte, et que la méthode n'est pas varargs, elle se verra attribuer une signature de convention d'appel optimisée basée sur ses champs `specTypes` et `rettype`.

Les principes généraux sont que :

  * Les types primitifs sont passés dans des registres int/float.
  * Les tuples de types VecElement sont passés dans des registres de vecteur.
  * Les structs sont passées sur la pile.
  * Les valeurs de retour sont traitées de manière similaire aux arguments, avec un seuil de taille au-delà duquel elles seront renvoyées via un argument sret caché.

La logique totale pour cela est implémentée par `get_specsig_function` et `deserves_sret`.

De plus, si le type de retour est une union, il peut être retourné sous la forme d'une paire de valeurs (un pointeur et une étiquette). Si les valeurs de l'union peuvent être allouées sur la pile, alors un espace suffisant pour les stocker sera également passé en tant que premier argument caché. Il appartient à l'appelé de décider si le pointeur retourné pointera vers cet espace, un objet encapsulé, ou même une autre mémoire constante.
