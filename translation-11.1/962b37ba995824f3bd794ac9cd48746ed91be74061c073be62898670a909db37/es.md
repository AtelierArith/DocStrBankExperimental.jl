# Fixing precompilation hangs due to open tasks or IO

En Julia 1.10 o superior, es posible que veas el siguiente mensaje:

![Captura de pantalla del bloqueo de precompilación](./img/precompilation_hang.png)

Esto puede repetirse. Si continúa repitiéndose sin indicios de que se resolverá por sí mismo, puede que tengas un "bloqueo de precompilación" que requiere ser solucionado. Incluso si es transitorio, puede que prefieras resolverlo para que los usuarios no se vean molestos por esta advertencia. Esta página te guía a través de cómo analizar y solucionar tales problemas.

Si sigues el consejo y presionas `Ctrl-C`, podrías ver

```
^C Interrupted: Exiting precompilation...

  1 dependency had warnings during precompilation:
┌ Test1 [ac89d554-e2ba-40bc-bc5c-de68b658c982]
│  [pid 2745] waiting for IO to finish:
│   Handle type        uv_handle_t->data
│   timer              0x55580decd1e0->0x7f94c3a4c340
```

Este mensaje transmite dos piezas clave de información:

  * el bloqueo está ocurriendo durante la precompilación de `Test1`, una dependencia de `Test2` (el paquete que estábamos intentando cargar con `using Test2`)
  * durante la precompilación de `Test1`, Julia creó un objeto `Timer` (usa `?Timer` si no estás familiarizado con los temporizadores) que aún está abierto; hasta que eso se cierre, el proceso está bloqueado.

Si esto es suficiente pista para que descubras cómo se está creando `timer = Timer(args...)`, una buena solución es agregar `wait(timer)` si `timer` eventualmente termina por sí mismo, o `close(timer)` si necesitas forzarlo a cerrarse, antes del `end` final del módulo.

Sin embargo, hay casos que pueden no ser tan sencillos. Por lo general, la mejor opción es comenzar por determinar si el bloqueo se debe al código en Test1 o si se debe a una de las dependencias de Test1:

  * Opción 1: `Pkg.add("Aqua")` y usa [`Aqua.test_persistent_tasks`](https://juliatesting.github.io/Aqua.jl/dev/#Aqua.test_persistent_tasks-Tuple{Base.PkgId}). Esto debería ayudarte a identificar qué paquete está causando el problema, después de lo cual se deben seguir las instrucciones [below](@ref pchang_fix). Si es necesario, puedes crear un `PkgId` como `Base.PkgId(UUID("..."), "Test1")`, donde `...` proviene de la entrada `uuid` en `Test1/Project.toml`.
  * Opción 2: diagnosticar manualmente la fuente del bloqueo.

Para diagnosticar manualmente:

1. `Pkg.desarrollar("Test1")`
2. Comment out all the code `include`d or defined in `Test1`, *except* the `using/import` statements.
3. Intenta `usar Test2` (o incluso `usar Test1` asumiendo que también se cuelga) de nuevo.

Ahora llegamos a una bifurcación en el camino: o bien

  * el retraso persiste, indicando que es [due to one of your dependencies](@ref pchang_deps)
  * el colgante desaparece, indicando que es [due to something in your code](@ref pchang_fix).

## [Diagnosing and fixing hangs due to a package dependency](@id pchang_deps)

Utiliza una búsqueda binaria para identificar la dependencia problemática: comienza comentando la mitad de tus dependencias, luego, cuando aísles cuál mitad es la responsable, comenta la mitad de esa mitad, etc. (No tienes que eliminarlas del proyecto, solo comenta las declaraciones `using`/`import`.)

Una vez que hayas identificado un sospechoso (aquí lo llamaremos `ThePackageYouThinkIsCausingTheProblem`), primero intenta precompilar ese paquete. Si también se queda colgado durante la precompilación, continúa rastreando el problema hacia atrás.

Sin embargo, lo más probable es que `ThePackageYouThinkIsCausingTheProblem` se compile correctamente. Esto sugiere que está en la función `ThePackageYouThinkIsCausingTheProblem.__init__`, que no se ejecuta durante la precompilación de `ThePackageYouThinkIsCausingTheProblem`, pero *sí* en cualquier paquete que cargue `ThePackageYouThinkIsCausingTheProblem`. Para probar esta teoría, configura un ejemplo mínimo funcional (MWE), algo como

```julia
(@v1.10) pkg> generate MWE
  Generating  project MWE:
    MWE\Project.toml
    MWE\src\MWE.jl
```

donde se encuentra el código fuente de `MWE.jl`

```julia
module MWE
using ThePackageYouThinkIsCausingTheProblem
end
```

y has agregado `ThePackageYouThinkIsCausingTheProblem` a las dependencias de MWE.

Si ese MWE reproduce el bloqueo, has encontrado a tu culpable: `ThePackageYouThinkIsCausingTheProblem.__init__` debe estar creando el objeto `Timer`. Si el objeto del temporizador se puede cerrar de manera segura, esa es una buena opción. De lo contrario, la solución más común es evitar crear el temporizador mientras *cualquier* paquete está siendo precompilado: añade

```julia
ccall(:jl_generating_output, Cint, ()) == 1 && return nothing
```

como la primera línea de `ThePackageYouThinkIsCausingTheProblem.__init__`, y evitará realizar cualquier inicialización en cualquier proceso de Julia cuyo propósito sea precompilar paquetes.

## [Fixing package code to avoid hangs](@id pchang_fix)

Busca en tu paquete palabras sugestivas (aquí como "Temporizador") y ve si puedes identificar dónde se está creando el problema. Ten en cuenta que una *definición* de método como

```julia
maketimer() = Timer(timer -> println("hi"), 0; interval=1)
```

no es problemático en sí mismo: solo puede causar este problema si `maketimer` se llama mientras se está definiendo el módulo. Esto podría estar sucediendo desde una declaración de nivel superior como

```julia
const GLOBAL_TIMER = maketimer()
```

o podría ocurrir conceiviblemente en un [precompile workload](https://github.com/JuliaLang/PrecompileTools.jl).

Si tienes dificultades para identificar las líneas causales, considera hacer una búsqueda binaria: comenta secciones de tu paquete (o líneas `include` para omitir archivos enteros) hasta que hayas reducido el problema en alcance.
