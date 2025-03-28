# Ahead of Time Compilation

Ce document décrit la conception et la structure du système de compilation à l'avance (AOT) dans Julia. Ce système est utilisé lors de la génération d'images système et d'images de paquets. Une grande partie de l'implémentation décrite ici se trouve dans `aotcompile.cpp`, `staticdata.c` et `processor.cpp`.

## Introduction

Bien que Julia compile normalement le code à la volée (JIT), il est possible de compiler le code à l'avance et d'enregistrer le code résultant dans un fichier. Cela peut être utile pour plusieurs raisons :

1. Pour réduire le temps nécessaire au démarrage d'un processus Julia.
2. Pour réduire le temps passé dans le compilateur JIT au lieu d'exécuter du code (temps jusqu'à la première exécution, TTFX).
3. Pour réduire la quantité de mémoire utilisée par le compilateur JIT.

## High-Level Overview

Les descriptions suivantes sont un aperçu des détails d'implémentation actuels du pipeline de bout en bout qui se déroule en interne lorsque l'utilisateur compile un nouveau module AOT, comme cela se produit lorsqu'il tape `using Foo`. Ces détails sont susceptibles de changer au fil du temps à mesure que nous mettons en œuvre de meilleures façons de les gérer, donc les implémentations actuelles peuvent ne pas correspondre exactement au flux de données et aux fonctions décrites ci-dessous.

### Compiling Code Images

Tout d'abord, les méthodes qui doivent être compilées en code natif doivent être identifiées. Cela ne peut être fait qu'en exécutant réellement le code à compiler, car l'ensemble des méthodes qui doivent être compilées dépend des types des arguments passés aux méthodes, et les invocations de méthodes avec certaines combinaisons de types peuvent ne pas être connues avant l'exécution. Au cours de ce processus, les méthodes exactes que le compilateur voit sont suivies pour une compilation ultérieure, produisant une trace de compilation.

!!! note
    Actuellement, lors de la compilation d'images, Julia exécute la génération de traces dans un processus différent de celui qui effectue la compilation AOT. Cela peut avoir des impacts lors de l'utilisation d'un débogueur pendant la précompilation. La meilleure façon de déboguer la précompilation avec un débogueur est d'utiliser le débogueur rr, d'enregistrer l'ensemble de l'arbre de processus, d'utiliser `rr ps` pour identifier le processus défaillant pertinent, puis d'utiliser `rr replay -p PID` pour rejouer uniquement le processus défaillant.


Une fois que les méthodes à compiler ont été identifiées, elles sont passées à la fonction `jl_create_system_image`. Cette fonction met en place un certain nombre de structures de données qui seront utilisées lors de la sérialisation du code natif dans un fichier, puis appelle `jl_create_native` avec le tableau de méthodes. `jl_create_native` exécute la génération de code sur les méthodes et produit un ou plusieurs modules LLVM. `jl_create_system_image` enregistre ensuite des informations utiles sur ce que la génération de code a produit à partir du ou des modules.

Les module(s) sont ensuite passés à `jl_dump_native`, avec les informations enregistrées par `jl_create_system_image`. `jl_dump_native` contient le code nécessaire pour sérialiser le(s) module(s) en bitcode, fichiers objets ou fichiers d'assemblage en fonction des options de ligne de commande passées à Julia. Le code sérialisé et les informations sont ensuite écrits dans un fichier sous forme d'archive.

La dernière étape consiste à exécuter un éditeur de liens système sur les fichiers objets dans l'archive produite par `jl_dump_native`. Une fois cette étape terminée, une bibliothèque partagée contenant le code compilé est produite.

### Loading Code Images

Lors du chargement d'une image de code, la bibliothèque partagée produite par l'éditeur de liens est chargée en mémoire. Les données de l'image système sont ensuite chargées à partir de la bibliothèque partagée. Ces données contiennent des informations sur les types, les méthodes et les instances de code qui ont été compilées dans la bibliothèque partagée. Ces données sont utilisées pour restaurer l'état de l'exécution à ce qu'il était lorsque l'image de code a été compilée.

Si l'image du code a été compilée avec du multiversioning, le chargeur choisira la version appropriée de chaque fonction à utiliser en fonction des fonctionnalités du CPU disponibles sur la machine actuelle.

Pour les images système, comme aucun autre code n'a été chargé, l'état de l'exécution est maintenant le même que lorsqu'une image de code a été compilée. Pour les images de paquet, l'environnement peut avoir changé par rapport à la compilation du code, donc chaque méthode doit être vérifiée par rapport à la table des méthodes globales pour déterminer si elle est toujours un code valide.

## Compiling Methods

### Tracing Compiled Methods

Julia a un drapeau en ligne de commande pour enregistrer toutes les méthodes qui sont compilées par le compilateur JIT, `--trace-compile=filename`. Lorsqu'une fonction est compilée et que ce drapeau a un nom de fichier, Julia imprimera une déclaration de précompilation dans ce fichier avec la méthode et les types d'arguments avec lesquels elle a été appelée. Cela génère donc un script de précompilation qui peut être utilisé plus tard dans le processus de compilation AOT. Le package [PrecompileTools](https://julialang.github.io/PrecompileTools.jl/stable/) dispose d'outils qui peuvent faciliter l'utilisation de cette fonctionnalité pour les développeurs de packages.

### `jl_create_system_image`

`jl_create_system_image` sauvegarde toutes les métadonnées spécifiques à Julia nécessaires pour restaurer ultérieurement l'état de l'exécution. Cela inclut des données telles que les instances de code, les instances de méthode, les tables de méthode et les informations de type. Cette fonction met également en place les structures de données nécessaires pour sérialiser le code natif dans un fichier. Enfin, elle appelle `jl_create_native` pour créer un ou plusieurs modules LLVM contenant le code natif pour les méthodes qui lui sont passées. `jl_create_native` est responsable de l'exécution de la génération de code sur les méthodes qui lui sont passées.

### `jl_dump_native`

`jl_dump_native` est responsable de la sérialisation du module LLVM contenant le code natif dans un fichier. En plus du module, les données de l'image système produites par `jl_create_system_image` sont compilées en tant que variable globale. La sortie de cette méthode est du bitcode, des objets et/ou des archives d'assemblage contenant le code et les données de l'image système.

`jl_dump_native` est généralement l'un des plus gros goulets d'étranglement lors de l'émission de code natif, une grande partie du temps étant consacrée à l'optimisation de l'IR LLVM et à l'émission de code machine. Par conséquent, cette fonction est capable de multithreader les étapes d'optimisation et d'émission de code machine. Ce multithreading est paramétré en fonction de la taille du module, mais peut être explicitement remplacé en définissant la variable d'environnement [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS). Le nombre maximum de threads par défaut est la moitié du nombre de threads disponibles, mais le réduire peut diminuer l'utilisation de la mémoire maximale pendant la compilation.

`jl_dump_native` peut également produire du code natif optimisé pour plusieurs architectures, lorsqu'il est intégré au chargeur Julia. Cela est déclenché en définissant la variable d'environnement [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) et médié par le passage de multiversionnement dans le pipeline d'optimisation. Pour que cela fonctionne avec le multithreading, une étape d'annotation est ajoutée avant que le module ne soit divisé en sous-modules qui sont émises sur leurs propres threads, et cette étape d'annotation utilise des informations disponibles dans l'ensemble du module pour décider quelles fonctions sont clonées pour différentes architectures. Une fois l'annotation effectuée, des threads individuels peuvent émettre du code pour différentes architectures en parallèle, sachant qu'une sous-module différente est garantie de produire les fonctions nécessaires qui seront appelées par une fonction clonée.

D'autres métadonnées sur la façon dont le module a été sérialisé sont également stockées dans l'archive, telles que le nombre de threads utilisés pour sérialiser le module et le nombre de fonctions qui ont été compilées.

### Static Linking

La dernière étape du processus de compilation AOT consiste à exécuter un éditeur de liens sur les fichiers objets dans l'archive produite par `jl_dump_native`. Cela produit une bibliothèque partagée contenant le code compilé. Cette bibliothèque partagée peut ensuite être chargée par Julia pour restaurer l'état de l'exécution. Lors de la compilation d'une image système, l'éditeur de liens natif utilisé par un compilateur C est utilisé pour produire la bibliothèque partagée finale. Pour les images de paquets, l'éditeur de liens LLVM LLD est utilisé pour fournir une interface de liaison plus cohérente.

## Loading Code Images

### Loading the Shared Library

La première étape pour charger une image de code consiste à charger la bibliothèque partagée produite par l'éditeur de liens. Cela se fait en appelant `jl_dlopen` sur le chemin de la bibliothèque partagée. Cette fonction est responsable du chargement de la bibliothèque partagée et de la résolution de tous les symboles dans la bibliothèque.

### Loading Native Code

Le chargeur doit d'abord identifier si le code natif qui a été compilé est valide pour l'architecture sur laquelle le chargeur s'exécute. Cela est nécessaire pour éviter d'exécuter des instructions que les anciens CPU ne reconnaissent pas. Cela se fait en vérifiant les fonctionnalités du CPU disponibles sur la machine actuelle par rapport aux fonctionnalités du CPU pour lesquelles le code a été compilé. Lorsque le multiversioning est activé, le chargeur choisira la version appropriée de chaque fonction à utiliser en fonction des fonctionnalités du CPU disponibles sur la machine actuelle. Si aucun des ensembles de fonctionnalités qui ont été multiversionnés, le chargeur renverra une erreur.

Une partie du passage de multiversioning crée un certain nombre de tableaux globaux de toutes les fonctions du module. Lorsque ce processus est multithreadé, un tableau de tableaux est créé, que le chargeur réorganise en un grand tableau contenant toutes les fonctions qui ont été compilées pour cette architecture. Un processus similaire se produit pour les variables globales dans le module.

### Setting Up Julia State

Le chargeur utilise ensuite les variables et fonctions globales produites par le chargement du code natif pour configurer les structures de données de base du runtime Julia dans le processus actuel. Cette configuration implique l'ajout de types et de méthodes au runtime Julia, et la mise à disposition du code natif mis en cache pour être utilisé par d'autres fonctions Julia et l'interpréteur. Pour les images de package, chaque méthode doit être validée, c'est-à-dire que l'état de la table des méthodes globales doit correspondre à l'état pour lequel l'image du package a été compilée. En particulier, si un ensemble différent de méthodes existe au moment du chargement par rapport au moment de la compilation de l'image du package, la méthode doit être invalidée et recompilée lors de sa première utilisation. Cela est nécessaire pour garantir que la sémantique d'exécution reste la même, que le package ait été précompilé ou que le code ait été exécuté directement. Les images système n'ont pas besoin d'effectuer cette validation, car la table des méthodes globales est vide au moment du chargement. Ainsi, les images système ont des temps de chargement plus rapides que les images de package.
