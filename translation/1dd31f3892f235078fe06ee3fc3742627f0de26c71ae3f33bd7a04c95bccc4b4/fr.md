```
worker_id_from_socket(s) -> pid
```

Une API de bas niveau qui, étant donné une connexion `IO` ou un `Worker`, renvoie le `pid` du worker auquel il est connecté. Cela est utile lors de l'écriture de méthodes [`serialize`](@ref) personnalisées pour un type, qui optimisent les données écrites en fonction de l'identifiant du processus récepteur.
