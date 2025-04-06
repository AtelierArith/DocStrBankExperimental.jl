```
Profile.take_heap_snapshot(filepath::String, all_one::Bool=false, streaming=false)
Profile.take_heap_snapshot(all_one::Bool=false; dir::String, streaming=false)
```

Écrivez un instantané du tas, dans le format JSON attendu par le visualiseur d'instantanés de tas des outils de développement Chrome (.heapsnapshot extension) dans un fichier (`$pid_$timestamp.heapsnapshot`) dans le répertoire courant par défaut (ou tempdir si le répertoire courant n'est pas accessible en écriture), ou dans `dir` si donné, ou le chemin de fichier complet donné, ou un flux IO.

Si `all_one` est vrai, alors signalez la taille de chaque objet comme un, afin qu'ils puissent être facilement comptés. Sinon, signalez la taille réelle.

Si `streaming` est vrai, nous allons diffuser les données de l'instantané dans quatre fichiers, en utilisant filepath comme préfixe, pour éviter de devoir conserver l'ensemble de l'instantané en mémoire. Cette option doit être utilisée pour tout paramètre où votre mémoire est limitée. Ces fichiers peuvent ensuite être réassemblés en appelant Profile.HeapSnapshot.assemble_snapshot(), ce qui peut être fait hors ligne.

REMARQUE : Nous recommandons fortement de définir streaming=true pour des raisons de performance. Reconstruire l'instantané à partir des parties nécessite de conserver l'ensemble de l'instantané en mémoire, donc si l'instantané est volumineux, vous pouvez manquer de mémoire lors de son traitement. Le streaming vous permet de reconstruire l'instantané hors ligne, après que votre charge de travail ait terminé de s'exécuter. Si vous essayez de collecter un instantané avec streaming=false (la valeur par défaut, pour des raisons de compatibilité ascendante) et que votre processus est tué, notez que cela enregistrera toujours les parties dans le même répertoire que votre chemin de fichier fourni, afin que vous puissiez toujours reconstruire l'instantané après coup, via `assemble_snapshot()`.
