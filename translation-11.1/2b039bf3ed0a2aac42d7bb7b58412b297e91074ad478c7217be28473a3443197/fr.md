```
Semaphore(sem_size)
```

Créez un sémaphore de comptage qui permet au maximum `sem_size` acquisitions d'être utilisées à tout moment. Chaque acquisition doit être assortie d'une libération.

Cela fournit un ordre de mémoire d'acquisition et de libération sur les appels d'acquisition/libération.
