# Using Valgrind with Julia

[Valgrind](https://valgrind.org/) es una herramienta para depuración de memoria, detección de fugas de memoria y perfilado. Esta sección describe cosas a tener en cuenta al usar Valgrind para depurar problemas de memoria con Julia.

## General considerations

Por defecto, Valgrind asume que no hay código que se modifica a sí mismo en los programas que ejecuta. Esta suposición funciona bien en la mayoría de los casos, pero falla miserablemente para un compilador just-in-time como `julia`. Por esta razón, es crucial pasar `--smc-check=all-non-file` a `valgrind`, de lo contrario, el código puede fallar o comportarse de manera inesperada (a menudo de formas sutiles).

En algunos casos, para detectar mejor los errores de memoria utilizando Valgrind, puede ser útil compilar `julia` con los grupos de memoria desactivados. La bandera de compilación `MEMDEBUG` desactiva los grupos de memoria en Julia, y `MEMDEBUG2` desactiva los grupos de memoria en FemtoLisp. Para compilar `julia` con ambas banderas, agrega la siguiente línea a `Make.user`:

```make
CFLAGS = -DMEMDEBUG -DMEMDEBUG2
```

Otra cosa a tener en cuenta: si tu programa utiliza múltiples procesos de trabajo, es probable que desees que todos esos procesos de trabajo se ejecuten bajo Valgrind, no solo el proceso principal. Para hacer esto, pasa `--trace-children=yes` a `valgrind`.

Otra cosa a tener en cuenta: si al usar `valgrind` aparece el error `Unable to find compatible target in system image`, intenta reconstruir la imagen del sistema con el objetivo `generic` o julia con `JULIA_CPU_TARGET=generic`.

## Suppressions

Valgrind normalmente mostrará advertencias espurias mientras se ejecuta. Para reducir el número de tales advertencias, ayuda proporcionar un [suppressions file](https://valgrind.org/docs/manual/manual-core.html#manual-core.suppress) a Valgrind. Un archivo de suprimidos de muestra está incluido en la distribución de origen de Julia en `contrib/valgrind-julia.supp`.

El archivo de supresiones se puede utilizar desde el directorio fuente `julia/` de la siguiente manera:

```
$ valgrind --smc-check=all-non-file --suppressions=contrib/valgrind-julia.supp ./julia progname.jl
```

Cualquier error de memoria que se muestre debe ser reportado como errores o contribuido como supresiones adicionales. Tenga en cuenta que algunas versiones de Valgrind son [shipped with insufficient default suppressions](https://github.com/JuliaLang/julia/issues/8314#issuecomment-55766210), así que eso puede ser algo a considerar antes de enviar cualquier error.

## Running the Julia test suite under Valgrind

Es posible ejecutar toda la suite de pruebas de Julia bajo Valgrind, pero toma bastante tiempo (típicamente varias horas). Para hacerlo, ejecuta el siguiente comando desde el directorio `julia/test/`:

```
valgrind --smc-check=all-non-file --trace-children=yes --suppressions=$PWD/../contrib/valgrind-julia.supp ../julia runtests.jl all
```

Si deseas ver un informe de fugas de memoria "definidas", pasa las banderas `--leak-check=full --show-leak-kinds=definite` a `valgrind` también.

## Additional spurious warnings

Esta sección cubre las advertencias de Valgrind que no se pueden agregar al archivo de supresiones, pero que, no obstante, son seguras de ignorar.

### Unhandled rr system calls

Valgrind emitirá una advertencia si encuentra alguno de los [system calls that are specific to rr](https://github.com/rr-debugger/rr/blob/master/src/preload/rrcalls.h), el [Record and Replay Framework](https://rr-project.org/). En particular, se mostrará una advertencia sobre una llamada al sistema `1008` no manejada cuando julia intente detectar si se está ejecutando bajo rr:

```
--xxxxxx-- WARNING: unhandled amd64-linux syscall: 1008
--xxxxxx-- You may be able to write your own handler.
--xxxxxx-- Read the file README_MISSING_SYSCALL_OR_IOCTL.
--xxxxxx-- Nevertheless we consider this a bug.  Please report
--xxxxxx-- it at http://valgrind.org/support/bug_reports.html.
```

Este problema [has been reported](https://bugs.kde.org/show_bug.cgi?id=446401) a los desarrolladores de Valgrind como han solicitado.

## Caveats

Valgrind actualmente [does not support multiple rounding modes](https://bugs.kde.org/show_bug.cgi?id=136779), por lo que el código que ajusta el modo de redondeo se comportará de manera diferente cuando se ejecute bajo Valgrind.

En general, si después de establecer `--smc-check=all-non-file` encuentras que tu programa se comporta de manera diferente cuando se ejecuta bajo Valgrind, puede ser útil pasar `--tool=none` a `valgrind` mientras investigas más a fondo. Esto habilitará la maquinaria mínima de Valgrind, pero también se ejecutará mucho más rápido que cuando se habilita el verificador de memoria completo.
