# ARM (Linux)

Julia admite completamente procesadores ARMv8 (AArch64) y admite ARMv7 y ARMv6 (AArch32) con algunas advertencias. Este archivo proporciona pautas generales para la compilación, además de instrucciones para dispositivos específicos.

Una lista de [known issues](https://github.com/JuliaLang/julia/labels/arm) para ARM está disponible. Si encuentras dificultades, por favor crea un problema incluyendo la salida de `cat /proc/cpuinfo`.

## 32-bit (ARMv6, ARMv7)

Julia se ha compilado con éxito en varias variantes de los siguientes dispositivos ARMv6 y ARMv7:

  * ARMv7 / Cortex A15 Chromebooks de Samsung ejecutando Ubuntu Linux bajo Crouton;
  * [Raspberry Pi](https://www.raspberrypi.org).
  * [Odroid](https://www.hardkernel.com).

Julia requiere al menos los conjuntos de instrucciones `armv6` y `vfpv2`. Se recomienda usar `armv7-a`. `armv5` o punto flotante suave no son compatibles.

### Raspberry Pi 1 / Raspberry Pi Zero

Si el tipo de CPU ARM utilizado en la Raspberry Pi no es detectado por LLVM, entonces establece explícitamente el objetivo de la CPU añadiendo lo siguiente a `Make.user`:

```
JULIA_CPU_TARGET=arm1176jzf-s
```

Para completar la construcción, es posible que necesites aumentar el tamaño del archivo de intercambio. Para hacerlo, edita `/etc/dphys-swapfile`, cambiando la línea:

```
CONF_SWAPSIZE=100
```

a:

```
CONF_SWAPSIZE=512
```

antes de reiniciar el servicio de swapfile:

```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```

### Raspberry Pi 2

El tipo de CPU ARM utilizado en la Raspberry Pi 2 no es detectado por LLVM. Establezca explícitamente el objetivo de la CPU añadiendo lo siguiente a `Make.user`:

`JULIA_CPU_TARGET=cortex-a7`

Dependiendo del compilador y la distribución exactos, puede haber un fallo en la compilación debido a ensamblaje en línea no soportado. En ese caso, añade `MCPU=armv7-a` a `Make.user`.

## AArch64 (ARMv8)

Julia se espera que trabaje y se construya en CPUs ARMv8. Se debe seguir la [build instructions](https://github.com/JuliaLang/julia/blob/master/README.md) general. Julia espera tener alrededor de 8GB de RAM o swap habilitado para construirse a sí misma.

### Known issues

A partir de Julia v1.10, [JITLink](https://llvm.org/docs/JITLink.html) está habilitado automáticamente en esta arquitectura para todos los sistemas operativos al vincularse con LLVM 15 o versiones posteriores. Debido a un [bug in LLVM memory manager](https://github.com/llvm/llvm-project/issues/63236), las cargas de trabajo no triviales pueden generar demasiados mapeos de memoria que en Linux pueden exceder el límite de mapeos de memoria (`mmap`) establecido en el archivo `/proc/sys/vm/max_map_count`, lo que resulta en un error como

```
JIT session error: Cannot allocate memory
```

Si esto sucede, pida a su administrador del sistema que aumente el límite de mapeos de memoria, por ejemplo, con el comando

```
sysctl -w vm.max_map_count=262144
```
