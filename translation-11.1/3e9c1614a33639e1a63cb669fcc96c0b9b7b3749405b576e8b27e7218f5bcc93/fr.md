```
TextDisplay(io::IO)
```

Renvoie un `TextDisplay <: AbstractDisplay`, qui affiche tout objet sous le type MIME text/plain (par défaut), en écrivant la représentation textuelle dans le flux I/O donné. (C'est ainsi que les objets sont imprimés dans le REPL Julia.)
