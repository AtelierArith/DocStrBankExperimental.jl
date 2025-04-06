```
free(addr::Ptr)
```

Appelle `free` de la bibliothèque standard C. N'utilisez cela que sur la mémoire obtenue à partir de [`malloc`](@ref), pas sur des pointeurs récupérés d'autres bibliothèques C. Les objets [`Ptr`](@ref) obtenus à partir de bibliothèques C doivent être libérés par les fonctions free définies dans cette bibliothèque, afin d'éviter des échecs d'assertion si plusieurs bibliothèques `libc` existent sur le système.
