```
Base.touch(::Pidfile.LockMonitor)
```

Met à jour le `mtime` sur le verrou, pour indiquer qu'il est toujours frais.

Voir aussi le mot-clé `refresh` dans le constructeur [`mkpidlock`](@ref).
