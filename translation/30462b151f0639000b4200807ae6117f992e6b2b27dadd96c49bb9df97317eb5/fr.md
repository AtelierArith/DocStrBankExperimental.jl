lock(f::Function, l::Lockable)

Acquérir le verrou associé à `l`, exécuter `f` avec le verrou détenu, et libérer le verrou lorsque `f` retourne. `f` recevra un argument positionnel : la valeur encapsulée par `l`. Si le verrou est déjà verrouillé par une autre tâche/fil, attendez qu'il devienne disponible. Lorsque cette fonction retourne, le `lock` a été libéré, donc l'appelant ne doit pas tenter de `unlock` le verrou.

!!! compat "Julia 1.11"
    Nécessite au moins Julia 1.11.

