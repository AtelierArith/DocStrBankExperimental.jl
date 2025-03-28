# ARM (Linux)

Julia unterstützt vollständig ARMv8 (AArch64) Prozessoren und unterstützt ARMv7 und ARMv6 (AArch32) mit einigen Einschränkungen. Diese Datei bietet allgemeine Richtlinien für die Kompilierung sowie Anweisungen für spezifische Geräte.

Eine Liste von [known issues](https://github.com/JuliaLang/julia/labels/arm) für ARM ist verfügbar. Wenn Sie auf Schwierigkeiten stoßen, erstellen Sie bitte ein Issue und fügen Sie die Ausgabe von `cat /proc/cpuinfo` bei.

## 32-bit (ARMv6, ARMv7)

Julia wurde erfolgreich auf mehreren Varianten der folgenden ARMv6- und ARMv7-Geräte kompiliert:

  * ARMv7 / Cortex A15 Samsung Chromebooks, die Ubuntu Linux unter Crouton ausführen;
  * [Raspberry Pi](https://www.raspberrypi.org)
  * [Odroid](https://www.hardkernel.com)

Julia benötigt mindestens die `armv6`- und `vfpv2`-Befehlssätze. Es wird empfohlen, `armv7-a` zu verwenden. `armv5` oder Soft-Float werden nicht unterstützt.

### Raspberry Pi 1 / Raspberry Pi Zero

Wenn der Typ der ARM-CPU, der im Raspberry Pi verwendet wird, von LLVM nicht erkannt wird, setzen Sie das CPU-Ziel explizit, indem Sie Folgendes zu `Make.user` hinzufügen:

```
JULIA_CPU_TARGET=arm1176jzf-s
```

Um den Build abzuschließen, müssen Sie möglicherweise die Größe der Swap-Datei erhöhen. Dazu bearbeiten Sie `/etc/dphys-swapfile` und ändern die Zeile:

```
CONF_SWAPSIZE=100
```

zu:

```
CONF_SWAPSIZE=512
```

bevor Sie den Swapfile-Dienst neu starten:

```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```

### Raspberry Pi 2

Der Typ der ARM-CPU, der im Raspberry Pi 2 verwendet wird, wird von LLVM nicht erkannt. Setzen Sie das CPU-Ziel explizit, indem Sie Folgendes zu `Make.user` hinzufügen:

`JULIA_CPU_TARGET=cortex-a7`

Je nach dem genauen Compiler und der Distribution kann es zu einem Build-Fehler aufgrund nicht unterstützter Inline-Assembly kommen. In diesem Fall fügen Sie `MCPU=armv7-a` zu `Make.user` hinzu.

## AArch64 (ARMv8)

Julia wird erwartet, dass sie auf ARMv8-CPUs arbeitet und darauf aufbaut. Man sollte der allgemeinen [build instructions](https://github.com/JuliaLang/julia/blob/master/README.md) folgen. Julia erwartet, dass etwa 8 GB RAM oder Swap aktiviert sind, um sich selbst zu bauen.

### Known issues

Ab Julia v1.10 ist [JITLink](https://llvm.org/docs/JITLink.html) automatisch für diese Architektur auf allen Betriebssystemen aktiviert, wenn mit LLVM 15 oder späteren Versionen verlinkt wird. Aufgrund eines [bug in LLVM memory manager](https://github.com/llvm/llvm-project/issues/63236) können nicht triviale Arbeitslasten zu vielen Speicherabbildungen führen, die unter Linux das Limit der Speicherabbildungen (`mmap`) überschreiten können, das in der Datei `/proc/sys/vm/max_map_count` festgelegt ist, was zu einem Fehler wie

```
JIT session error: Cannot allocate memory
```

Sollte dies geschehen, bitten Sie Ihren Systemadministrator, das Limit der Speichermappings zu erhöhen, beispielsweise mit dem Befehl

```
sysctl -w vm.max_map_count=262144
```
