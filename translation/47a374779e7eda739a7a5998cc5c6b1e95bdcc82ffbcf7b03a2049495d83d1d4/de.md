```
LibGit2.SignatureStruct
```

Eine Aktionssignatur (z. B. für Committer, Tagger usw.). Entspricht der [`git_signature`](https://libgit2.org/libgit2/#HEAD/type/git_signature) Struktur.

Die Felder repräsentieren:

  * `name`: Der vollständige Name des Committers oder Autors des Commits.
  * `email`: Die E-Mail-Adresse, unter der der Committer/Autor kontaktiert werden kann.
  * `when`: eine [`TimeStruct`](@ref), die angibt, wann der Commit in das Repository verfasst/committed wurde.
