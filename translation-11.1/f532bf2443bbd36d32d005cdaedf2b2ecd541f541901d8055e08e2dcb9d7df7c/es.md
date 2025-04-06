Nota especial para [`Threads.Condition`](@ref):

El llamador debe estar sosteniendo el [`lock`](@ref) que posee un `Threads.Condition` antes de llamar a este método. La tarea que llama estará bloqueada hasta que otra tarea la despierte, generalmente llamando a [`notify`](@ref) en el mismo objeto `Threads.Condition`. El lock se liberará de forma atómica al bloquearse (incluso si estaba bloqueado recursivamente) y se volverá a adquirir antes de regresar.
