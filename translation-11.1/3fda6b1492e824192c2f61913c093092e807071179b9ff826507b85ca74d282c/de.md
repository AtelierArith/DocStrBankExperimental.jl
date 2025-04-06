```
artifact_path(hash::SHA1; honor_overrides::Bool=true)
```

Gibt den Installationspfad eines Artefakts (identifiziert durch den SHA1-Git-Baum-Hash) zurück. Wenn das Artefakt nicht existiert, wird der Ort zurückgegeben, an dem es installiert werden würde.

!!! compat "Julia 1.3"
    Diese Funktion erfordert mindestens Julia 1.3.

