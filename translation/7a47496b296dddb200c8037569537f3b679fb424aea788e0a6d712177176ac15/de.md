```
LibGit2.FetchHead
```

Enthält die Informationen über HEAD während eines Fetch, einschließlich des Namens und der URL des Branches, von dem abgerufen wurde, der oid des HEAD und ob der abgerufene HEAD lokal zusammengeführt wurde.

Die Felder repräsentieren:

  * `name`: Der Name in der lokalen Referenzdatenbank des Fetch-Head, zum Beispiel `"refs/heads/master"`.
  * `url`: Die URL des Fetch-Head.
  * `oid`: Der [`GitHash`](@ref) des Tipps des Fetch-Head.
  * `ismerge`: Boolean-Flag, das angibt, ob die Änderungen am Remote bereits in die lokale Kopie zusammengeführt wurden oder nicht. Wenn `true`, ist die lokale Kopie mit dem Remote-Fetch-Head auf dem neuesten Stand.
