# Parallel Computing

Julia admite estas cuatro categorías de programación concurrente y paralela:

1. **"Tareas" asíncronas, o corutinas**:

    Las tareas de Julia permiten suspender y reanudar cálculos para I/O, manejo de eventos, procesos productor-consumidor y patrones similares. Las tareas pueden sincronizarse a través de operaciones como [`wait`](@ref) y [`fetch`](@ref), y comunicarse a través de [`Channel`](@ref)s. Si bien estrictamente no son computación paralela por sí mismas, Julia te permite programar [`Task`](@ref)s en varios hilos.
2. **Multi-hilo**:

    La [multi-threading](@ref man-multithreading) de Julia proporciona la capacidad de programar tareas simultáneamente en más de un hilo o núcleo de CPU, compartiendo memoria. Esta es generalmente la forma más fácil de obtener paralelismo en una PC o en un solo servidor grande de múltiples núcleos. El multi-hilo de Julia es composable. Cuando una función multi-hilo llama a otra función multi-hilo, Julia programará todos los hilos globalmente en los recursos disponibles, sin sobrecargar.
3. **Computación distribuida**:

    La computación distribuida ejecuta múltiples procesos de Julia con espacios de memoria separados. Estos pueden estar en la misma computadora o en múltiples computadoras. La biblioteca estándar [`Distributed`](@ref man-distributed) proporciona la capacidad para la ejecución remota de una función de Julia. Con este bloque de construcción básico, es posible construir muchos tipos diferentes de abstracciones de computación distribuida. Paquetes como [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) son un ejemplo de tal abstracción. Por otro lado, paquetes como [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) y [`Elemental.jl`](https://github.com/JuliaParallel/Elemental.jl) proporcionan acceso al ecosistema existente de bibliotecas MPI.
4. **Computación GPU**:

    El compilador de GPU de Julia proporciona la capacidad de ejecutar código Julia de forma nativa en GPUs. Hay un rico ecosistema de paquetes de Julia que están dirigidos a GPUs. El [JuliaGPU.org](https://juliagpu.org) sitio web proporciona una lista de capacidades, GPUs soportadas, paquetes relacionados y documentación.
