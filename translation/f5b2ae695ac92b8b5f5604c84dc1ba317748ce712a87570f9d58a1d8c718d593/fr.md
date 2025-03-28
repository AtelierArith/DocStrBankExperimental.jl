```
disable_sigint(f::Function)
```

Désactive le gestionnaire Ctrl-C pendant l'exécution d'une fonction sur la tâche actuelle, pour appeler du code externe qui peut appeler du code julia qui n'est pas sûr pour les interruptions. Destiné à être appelé en utilisant la syntaxe de bloc `do` comme suit :

```
disable_sigint() do
    # code non sûr pour les interruptions
    ...
end
```

Cela n'est pas nécessaire sur les threads de travail (`Threads.threadid() != 1`) puisque l'`InterruptException` ne sera livrée qu'au thread maître. Les fonctions externes qui n'appellent pas de code julia ou le runtime julia désactivent automatiquement sigint pendant leur exécution.
