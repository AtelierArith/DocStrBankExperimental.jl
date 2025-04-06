```
kill(p::Process, signum=Base.SIGTERM)
```

Envoyer un signal à un processus. La valeur par défaut est de terminer le processus. Renvoie avec succès si le processus a déjà quitté, mais lance une erreur si la terminaison du processus a échoué pour d'autres raisons (par exemple, permissions insuffisantes).
