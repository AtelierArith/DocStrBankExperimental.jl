```
ffmerge!(repo::GitRepo, ann::GitAnnotated)
```

Schnellvorlauf-Merge-Änderungen in den aktuellen HEAD. Dies ist nur möglich, wenn der Commit, auf den sich `ann` bezieht, von dem aktuellen HEAD abstammt (z. B. wenn Änderungen von einem Remote-Branch abgerufen werden, der einfach vor der Spitze des lokalen Branches liegt).
