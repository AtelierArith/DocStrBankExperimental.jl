# JIT Design and Implementation

Ce document explique la conception et la mise en œuvre du JIT de Julia, après que la génération de code soit terminée et que l'IR LLVM non optimisé ait été produit. Le JIT est responsable de l'optimisation et de la compilation de cet IR en code machine, ainsi que de son intégration dans le processus actuel et de la mise à disposition du code pour l'exécution.

## Introduction

Le JIT est responsable de la gestion des ressources de compilation, de la recherche de code précédemment compilé et de la compilation de nouveau code. Il est principalement construit sur la technologie [On-Request-Compilation](https://llvm.org/docs/ORCv2.html) d'LLVM (ORCv2), qui offre un support pour un certain nombre de fonctionnalités utiles telles que la compilation concurrente, la compilation paresseuse et la capacité de compiler du code dans un processus séparé. Bien qu'LLVM fournisse un compilateur JIT de base sous la forme de LLJIT, Julia utilise de nombreuses API ORCv2 directement pour créer son propre compilateur JIT personnalisé.

## Overview

![Diagramme du flux du compilateur](./img/compiler_diagram.png)

Codegen produit un module LLVM contenant du IR pour une ou plusieurs fonctions Julia à partir du IR SSA Julia original produit par l'inférence de type (étiqueté comme traduction sur le diagramme du compilateur ci-dessus). Il produit également une correspondance entre l'instance de code et le nom de la fonction LLVM. Cependant, bien que certaines optimisations aient été appliquées par le compilateur basé sur Julia sur le IR Julia, le IR LLVM produit par codegen contient encore de nombreuses opportunités d'optimisation. Ainsi, la première étape que le JIT effectue est d'exécuter un pipeline d'optimisation indépendant de la cible[^tdp] sur le module LLVM. Ensuite, le JIT exécute un pipeline d'optimisation dépendant de la cible, qui inclut des optimisations spécifiques à la cible et la génération de code, et produit un fichier objet. Enfin, le JIT lie le fichier objet résultant au processus en cours et rend le code disponible pour l'exécution. Tout cela est contrôlé par du code dans `src/jitlayers.cpp`.

[^tdp]: This is not a totally-target independent pipeline, as transformations such as vectorization rely upon target information such as vector register width and cost modeling. Additionally, codegen itself makes a few target-dependent assumptions, and the optimization pipeline will take advantage of that knowledge.

Actuellement, un seul thread à la fois est autorisé à entrer dans le pipeline d'optimisation-compilation-liaison, en raison des restrictions imposées par l'un de nos lieurs (RuntimeDyld). Cependant, le JIT est conçu pour prendre en charge l'optimisation et la compilation concurrentes, et la restriction du lieur devrait être levée à l'avenir lorsque RuntimeDyld aura été entièrement remplacé sur toutes les plateformes.

## Optimization Pipeline

Le pipeline d'optimisation est basé sur le nouveau gestionnaire de passes d'LLVM, mais le pipeline est personnalisé pour les besoins de Julia. Le pipeline est défini dans `src/pipeline.cpp`, et se déroule en plusieurs étapes comme détaillé ci-dessous.

1. Simplification précoce

    1. Ces passes sont principalement utilisées pour simplifier l'IR et canoniser les motifs afin que les passes ultérieures puissent identifier ces motifs plus facilement. De plus, divers appels intrinsèques tels que les indices de prédiction de branche et les annotations sont réduits en d'autres métadonnées ou d'autres caractéristiques de l'IR. [`SimplifyCFG`](https://llvm.org/docs/Passes.html#simplifycfg-simplify-the-cfg) (simplifier le graphe de contrôle de flux), [`DCE`](https://llvm.org/docs/Passes.html#dce-dead-code-elimination) (élimination de code mort), et [`SROA`](https://llvm.org/docs/Passes.html#sroa-scalar-replacement-of-aggregates) (remplacement scalaire des agrégats) sont quelques-uns des acteurs clés ici.
2. Optimisation précoce

    1. Ces passes sont généralement peu coûteuses et se concentrent principalement sur la réduction du nombre d'instructions dans l'IR et la propagation des connaissances à d'autres instructions. Par exemple, [`EarlyCSE`](https://en.wikipedia.org/wiki/Common_subexpression_elimination) est utilisé pour effectuer l'élimination des sous-expressions communes, et [`InstCombine`](https://llvm.org/docs/Passes.html#instcombine-combine-redundant-instructions) et [`InstSimplify`](https://llvm.org/doxygen/classllvm_1_1InstSimplifyPass.html#details) effectuent un certain nombre de petites optimisations de peephole pour rendre les opérations moins coûteuses.
3. Optimisation de boucle

    1. Ces passes canonisent et simplifient les boucles. Les boucles sont souvent du code chaud, ce qui rend l'optimisation des boucles extrêmement importante pour la performance. Les acteurs clés ici incluent [`LoopRotate`](https://llvm.org/docs/Passes.html#loop-rotate-rotate-loops), [`LICM`](https://llvm.org/docs/Passes.html#licm-loop-invariant-code-motion), et [`LoopFullUnroll`](https://llvm.org/docs/Passes.html#loop-unroll-unroll-loops). Certaines éliminations de vérification des limites se produisent également ici, en raison du passage [`IRCE`](https://llvm.org/doxygen/InductiveRangeCheckElimination_8cpp_source.html) qui peut prouver que certaines limites ne sont jamais dépassées.
4. Optimisation scalaire

    1. Le pipeline d'optimisation scalaire contient un certain nombre de passes plus coûteuses, mais plus puissantes, telles que [`GVN`](https://llvm.org/docs/Passes.html#gvn-global-value-numbering) (numérotation de valeur globale), [`SCCP`](https://llvm.org/docs/Passes.html#sccp-sparse-conditional-constant-propagation) (propagation conditionnelle constante sparse), et un autre tour d'élimination des vérifications de limites. Ces passes sont coûteuses, mais elles peuvent souvent supprimer de grandes quantités de code et rendre la vectorisation beaucoup plus réussie et efficace. Plusieurs autres passes de simplification et d'optimisation s'entremêlent avec les plus coûteuses pour réduire la quantité de travail qu'elles ont à faire.
5. Vectorisation

    1. [Automatic vectorization](https://en.wikipedia.org/wiki/Automatic_vectorization) est une transformation extrêmement puissante pour le code intensif en CPU. En bref, la vectorisation permet l'exécution d'une [single instruction on multiple data](https://en.wikipedia.org/wiki/Single_instruction,_multiple_data) (SIMD), par exemple, en effectuant 8 opérations d'addition en même temps. Cependant, prouver que le code est à la fois capable de vectorisation et rentable à vectoriser est difficile, et cela repose fortement sur les passes d'optimisation antérieures pour transformer l'IR dans un état où la vectorisation en vaut la peine.
6. Baisse intrinsèque

    1. Julia insère un certain nombre d'intrinsèques personnalisées, pour des raisons telles que l'allocation d'objets, la collecte des ordures et la gestion des exceptions. Ces intrinsèques ont été initialement placées pour rendre les opportunités d'optimisation plus évidentes, mais elles sont maintenant abaissées en IR LLVM pour permettre à l'IR d'être émis en tant que code machine.
7. Nettoyage

    1. Ces passes sont des optimisations de dernière chance et effectuent de petites optimisations telles que la propagation de multiplication-addition fusionnée et la simplification de division-reste. De plus, les cibles qui ne prennent pas en charge les nombres à virgule flottante de demi-précision verront leurs instructions de demi-précision converties en instructions de simple précision ici, et des passes sont ajoutées pour fournir un support de désinfection.

## Target-Dependent Optimization and Code Generation

LLVM fournit une optimisation et une génération de code machine dépendantes de la cible dans le même pipeline, situé dans le TargetMachine pour une plateforme donnée. Ces passes incluent la sélection d'instructions, la planification d'instructions, l'allocation de registres et l'émission de code machine. La documentation LLVM offre un bon aperçu du processus, et le code source LLVM est le meilleur endroit pour chercher des détails sur le pipeline et les passes.

## Linking

Actuellement, Julia est en train de passer entre deux linkers : l'ancien linker RuntimeDyld et le nouveau linker [JITLink](https://llvm.org/docs/JITLink.html). JITLink contient un certain nombre de fonctionnalités que RuntimeDyld n'a pas, telles que le linking concurrent et réentrant, mais manque actuellement d'un bon support pour les intégrations de profilage et ne prend pas encore en charge toutes les plateformes que RuntimeDyld prend en charge. Au fil du temps, JITLink devrait remplacer complètement RuntimeDyld. D'autres détails sur JITLink peuvent être trouvés dans la documentation LLVM.

## Execution

Une fois que le code a été lié au processus actuel, il est disponible pour exécution. Ce fait est porté à la connaissance du code générant `codeinst` en mettant à jour les champs `invoke`, `specsigflags` et `specptr` de manière appropriée. Les `codeinsts` prennent en charge la mise à niveau des champs `invoke`, `specsigflags` et `specptr`, tant que chaque combinaison de ces champs qui existe à un moment donné est valide pour être appelée. Cela permet au JIT de mettre à jour ces champs sans invalider les `codeinsts` existants, soutenant un potentiel JIT concurrent futur. Plus précisément, les états suivants peuvent être valides :

1. `invoke` est NULL, `specsigflags` est 0b00, `specptr` est NULL

    1. Ceci est l'état initial d'un codeinst, et indique que le codeinst n'a pas encore été compilé.
2. `invoke` n'est pas nul, `specsigflags` est 0b00, `specptr` est NULL

    1. Cela indique que le codeinst n'a pas été compilé avec une spécialisation, et que le codeinst doit être invoqué directement. Notez que dans ce cas, `invoke` ne lit ni les champs `specsigflags` ni `specptr`, et par conséquent, ils peuvent être modifiés sans invalider le pointeur `invoke`.
3. `invoke` est non nul, `specsigflags` est 0b10, `specptr` est non nul

    1. Cela indique que le code a été compilé, mais qu'une signature de fonction spécialisée a été jugée inutile par le codegen.
4. `invoke` est non nul, `specsigflags` est 0b11, `specptr` est non nul

    1. Cela indique que le codeinst a été compilé et qu'une signature de fonction spécialisée a été jugée nécessaire par le codegen. Le champ `specptr` contient un pointeur vers la signature de fonction spécialisée. Le pointeur `invoke` est autorisé à lire à la fois les champs `specsigflags` et `specptr`.

De plus, il existe un certain nombre d'états transitoires différents qui se produisent pendant le processus de mise à jour. Pour tenir compte de ces situations potentielles, les modèles d'écriture et de lecture suivants doivent être utilisés lors de la gestion de ces champs codeinst.

1. Lors de l'écriture de `invoke`, `specsigflags` et `specptr` :

    1. Effectuez une opération de comparaison-échange atomique de specptr en supposant que l'ancienne valeur était NULL. Cette opération de comparaison-échange doit avoir au moins un ordre d'acquisition-libération, afin de fournir des garanties d'ordre des opérations mémoire restantes dans l'écriture.
    2. Si `specptr` n'était pas nul, cessez l'opération d'écriture et attendez que le bit 0b10 de `specsigflags` soit écrit.
    3. Écrivez le nouveau bit bas de `specsigflags` à sa valeur finale. Cela peut être une écriture relâchée.
    4. Écrivez le nouveau pointeur `invoke` à sa valeur finale. Cela doit avoir au moins un ordre de mémoire de libération pour se synchroniser avec les lectures de `invoke`.
    5. Définissez le deuxième bit de `specsigflags` sur 1. Cela doit être au moins un ordre de mémoire de libération pour se synchroniser avec les lectures de `specsigflags`. Cette étape complète l'opération d'écriture et annonce à tous les autres threads que tous les champs ont été définis.
2. Lors de la lecture de `invoke`, `specsigflags` et `specptr` :

    1. Lisez le champ `invoke` avec au moins un ordre de mémoire d'acquisition. Ce chargement sera appelé `initial_invoke`.
    2. Si `initial_invoke` est NULL, le codeinst n'est pas encore exécutable. `invoke` est NULL, `specsigflags` peut être traité comme 0b00, `specptr` peut être traité comme NULL.
    3. Lisez le champ `specptr` avec au moins un ordre de mémoire d'acquisition.
    4. Si `specptr` est NULL, alors le pointeur `initial_invoke` ne doit pas dépendre de `specptr` pour garantir une exécution correcte. Par conséquent, `invoke` est non nul, `specsigflags` peut être traité comme 0b00, `specptr` peut être traité comme NULL.
    5. Si `specptr` n'est pas nul, alors `initial_invoke` pourrait ne pas être le champ `invoke` final qui utilise `specptr`. Cela peut se produire si `specptr` a été écrit, mais que `invoke` n'a pas encore été écrit. Par conséquent, tournez sur le deuxième bit de `specsigflags` jusqu'à ce qu'il soit défini sur 1 avec au moins un ordre de mémoire d'acquisition.
    6. Relisez le champ `invoke` avec au moins un ordre de mémoire d'acquisition. Ce chargement sera appelé `final_invoke`.
    7. Lisez le champ `specsigflags` avec n'importe quel ordre de mémoire.
    8. `invoke` est `final_invoke`, `specsigflags` est la valeur lue à l'étape 7, `specptr` est la valeur lue à l'étape 3.
3. Lors de la mise à jour d'un `specptr` vers un autre pointeur de fonction différent mais équivalent :

    1. Effectuez un stockage de libération du nouveau pointeur de fonction vers `specptr`. Les courses ici doivent être bénignes, car l'ancien pointeur de fonction doit rester valide, et tous les nouveaux doivent également être valides. Une fois qu'un pointeur a été écrit dans `specptr`, il doit toujours être appelable, qu'il soit ou non écrasé par la suite.

Bien que ces étapes d'écriture, de lecture et de mise à jour soient compliquées, elles garantissent que le JIT peut mettre à jour les codeinsts sans invalider les codeinsts existants, et que le JIT peut mettre à jour les codeinsts sans invalider les pointeurs `invoke` existants. Cela permet au JIT de potentiellement réoptimiser les fonctions à des niveaux d'optimisation plus élevés à l'avenir, et permettra également au JIT de prendre en charge la compilation concurrente des fonctions à l'avenir.
