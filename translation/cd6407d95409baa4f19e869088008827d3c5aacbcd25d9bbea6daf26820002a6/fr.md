```
moduleroot(m::Module) -> Module
```

Trouvez le module racine d'un module donné. C'est le premier module dans la chaîne des modules parents de `m` qui est soit un module racine enregistré, soit qui est son propre module parent.
