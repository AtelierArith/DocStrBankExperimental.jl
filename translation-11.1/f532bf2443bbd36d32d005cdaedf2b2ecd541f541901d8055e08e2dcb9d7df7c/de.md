Besondere Anmerkung für [`Threads.Condition`](@ref):

Der Aufrufer muss den [`lock`](@ref) halten, der ein `Threads.Condition` besitzt, bevor er diese Methode aufruft. Die aufrufende Aufgabe wird blockiert, bis eine andere Aufgabe sie weckt, normalerweise durch den Aufruf von [`notify`](@ref) auf demselben `Threads.Condition`-Objekt. Der Lock wird atomar freigegeben, wenn die Blockierung erfolgt (auch wenn er rekursiv gesperrt war), und wird vor der Rückkehr erneut erworben.
