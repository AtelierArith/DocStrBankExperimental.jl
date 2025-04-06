```
launch(manager::ClusterManager, params::Dict, launched::Array, launch_ntfy::Condition)
```

Implementiert von Cluster-Managern. Für jeden Julia-Arbeiter, der von dieser Funktion gestartet wird, sollte ein `WorkerConfig`-Eintrag zu `launched` hinzugefügt und `launch_ntfy` benachrichtigt werden. Die Funktion MUSS beenden, sobald alle Arbeiter, die von `manager` angefordert wurden, gestartet wurden. `params` ist ein Wörterbuch aller Schlüsselargumente, mit denen [`addprocs`](@ref) aufgerufen wurde.
