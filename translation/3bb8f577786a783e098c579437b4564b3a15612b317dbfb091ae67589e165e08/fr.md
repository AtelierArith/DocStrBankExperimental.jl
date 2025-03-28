```
windowserror(sysfunc[, code::UInt32=Libc.GetLastError()])
windowserror(sysfunc, iftrue::Bool)
```

Comme [`systemerror`](@ref), mais pour les fonctions de l'API Windows qui utilisent [`GetLastError`](@ref Base.Libc.GetLastError) pour retourner un code d'erreur au lieu de définir [`errno`](@ref Base.Libc.errno).
