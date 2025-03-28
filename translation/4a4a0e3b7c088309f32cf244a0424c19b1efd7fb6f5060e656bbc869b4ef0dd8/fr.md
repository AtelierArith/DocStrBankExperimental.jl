```
RawFD
```

Type primitif qui enveloppe le descripteur de fichier natif du système d'exploitation. Les `RawFD` peuvent être passés à des méthodes comme [`stat`](@ref) pour découvrir des informations sur le fichier sous-jacent, et peuvent également être utilisés pour ouvrir des flux, le `RawFD` décrivant le fichier du système d'exploitation soutenant le flux.
