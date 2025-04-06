Note spéciale pour [`Threads.Condition`](@ref) :

L'appelant doit détenir le [`lock`](@ref) qui possède un `Threads.Condition` avant d'appeler cette méthode. La tâche appelante sera bloquée jusqu'à ce qu'une autre tâche la réveille, généralement en appelant [`notify`](@ref) sur le même objet `Threads.Condition`. Le verrou sera libéré de manière atomique lors du blocage (même s'il était verrouillé de manière récursive) et sera réacquis avant le retour.
