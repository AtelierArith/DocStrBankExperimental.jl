```
fetch(rmt::GitRemote, refspecs; options::FetchOptions=FetchOptions(), msg="")
```

Holen Sie von dem angegebenen `rmt` Remote-Git-Repository ab, wobei `refspecs` verwendet wird, um zu bestimmen, welche Remote-Branch(es) abgerufen werden sollen. Die Schlüsselwortargumente sind:

  * `options`: bestimmt die Optionen für den Abruf, z. B. ob danach bereinigt werden soll. Siehe [`FetchOptions`](@ref) für weitere Informationen.
  * `msg`: eine Nachricht, die in die Reflogs eingefügt werden soll.
