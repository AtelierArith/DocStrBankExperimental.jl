# ARM (Linux)

Julia prend en charge pleinement les processeurs ARMv8 (AArch64) et prend en charge ARMv7 et ARMv6 (AArch32) avec quelques réserves. Ce fichier fournit des directives générales pour la compilation, en plus des instructions pour des appareils spécifiques.

Une liste de [known issues](https://github.com/JuliaLang/julia/labels/arm) pour ARM est disponible. Si vous rencontrez des difficultés, veuillez créer un problème en incluant la sortie de `cat /proc/cpuinfo`.

## 32-bit (ARMv6, ARMv7)

Julia a été compilé avec succès sur plusieurs variantes des appareils suivants ARMv6 et ARMv7 :

  * ARMv7 / Cortex A15 Chromebooks Samsung fonctionnant sous Ubuntu Linux avec Crouton ;
  * [Raspberry Pi](https://www.raspberrypi.org).
  * [Odroid](https://www.hardkernel.com).

Julia nécessite au moins les ensembles d'instructions `armv6` et `vfpv2`. Il est recommandé d'utiliser `armv7-a`. `armv5` ou le float logiciel ne sont pas pris en charge.

### Raspberry Pi 1 / Raspberry Pi Zero

Si le type de CPU ARM utilisé dans le Raspberry Pi n'est pas détecté par LLVM, définissez explicitement la cible du CPU en ajoutant ce qui suit à `Make.user` :

```
JULIA_CPU_TARGET=arm1176jzf-s
```

Pour compléter la construction, vous devrez peut-être augmenter la taille du fichier d'échange. Pour ce faire, modifiez `/etc/dphys-swapfile`, en changeant la ligne :

```
CONF_SWAPSIZE=100
```

à :

```
CONF_SWAPSIZE=512
```

avant de redémarrer le service swapfile :

```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```

### Raspberry Pi 2

Le type de CPU ARM utilisé dans le Raspberry Pi 2 n'est pas détecté par LLVM. Définissez explicitement la cible du CPU en ajoutant ce qui suit à `Make.user` :

`JULIA_CPU_TARGET=cortex-a7`

Selon le compilateur et la distribution exacts, il peut y avoir un échec de la construction en raison d'un assemblage en ligne non pris en charge. Dans ce cas, ajoutez `MCPU=armv7-a` à `Make.user`.

## AArch64 (ARMv8)

Julia est censée fonctionner et se développer sur des processeurs ARMv8. Il convient de suivre la [build instructions](https://github.com/JuliaLang/julia/blob/master/README.md) générale. Julia s'attend à avoir environ 8 Go de RAM ou d'échange activé pour se construire.

### Known issues

À partir de Julia v1.10, [JITLink](https://llvm.org/docs/JITLink.html) est automatiquement activé sur cette architecture pour tous les systèmes d'exploitation lors de la liaison à LLVM 15 ou des versions ultérieures. En raison d'un [bug in LLVM memory manager](https://github.com/llvm/llvm-project/issues/63236), des charges de travail non triviales peuvent générer trop de mappages mémoire qui, sur Linux, peuvent dépasser la limite de mappages mémoire (`mmap`) définie dans le fichier `/proc/sys/vm/max_map_count`, entraînant une erreur comme

```
JIT session error: Cannot allocate memory
```

Si cela se produit, demandez à votre administrateur système d'augmenter la limite des mappages de mémoire par exemple avec la commande

```
sysctl -w vm.max_map_count=262144
```
