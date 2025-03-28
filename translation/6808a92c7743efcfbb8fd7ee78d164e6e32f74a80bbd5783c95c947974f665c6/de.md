```
Modul
```

Ein `Modul` ist ein separater globaler Variablenarbeitsbereich. Siehe [`module`](@ref) und den [Handbuchabschnitt über Module](@ref modules) für Details.

```
Module(name::Symbol=:anonymous, std_imports=true, default_names=true)
```

Gibt ein Modul mit dem angegebenen Namen zurück. Ein `baremodule` entspricht `Module(:ModuleName, false)`

Ein leeres Modul, das überhaupt keine Namen enthält, kann mit `Module(:ModuleName, false, false)` erstellt werden. Dieses Modul importiert weder `Base` noch `Core` und enthält keinen Verweis auf sich selbst.
