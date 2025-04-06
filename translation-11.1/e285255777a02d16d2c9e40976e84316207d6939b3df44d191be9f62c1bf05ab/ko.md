# ARM (Linux)

Julia는 ARMv8 (AArch64) 프로세서를 완전히 지원하며, ARMv7 및 ARMv6 (AArch32)도 일부 주의사항과 함께 지원합니다. 이 파일은 특정 장치에 대한 지침 외에도 컴파일에 대한 일반적인 지침을 제공합니다.

[known issues](https://github.com/JuliaLang/julia/labels/arm)에 대한 ARM용 목록이 제공됩니다. 문제가 발생하면 `cat /proc/cpuinfo`의 출력을 포함하여 이슈를 생성해 주시기 바랍니다.

## 32-bit (ARMv6, ARMv7)

Julia는 다음 ARMv6 및 ARMv7 장치의 여러 변형에서 성공적으로 컴파일되었습니다:

  * ARMv7 / Cortex A15 삼성 크롬북에서 Crouton을 사용하여 우분투 리눅스 실행;
  * [Raspberry Pi](https://www.raspberrypi.org)
  * [Odroid](https://www.hardkernel.com)

Julia는 최소한 `armv6` 및 `vfpv2` 명령어 세트를 요구합니다. `armv7-a`를 사용하는 것이 권장됩니다. `armv5` 또는 소프트 플로트는 지원되지 않습니다.

### Raspberry Pi 1 / Raspberry Pi Zero

ARM CPU가 Raspberry Pi에서 사용되는 유형이 LLVM에 의해 감지되지 않는 경우, `Make.user`에 다음을 추가하여 CPU 대상을 명시적으로 설정하십시오:

```
JULIA_CPU_TARGET=arm1176jzf-s
```

빌드를 완료하려면 스왑 파일 크기를 늘려야 할 수 있습니다. 그렇게 하려면 `/etc/dphys-swapfile`를 편집하고 다음 줄을 변경하세요:

```
CONF_SWAPSIZE=100
```

로:

```
CONF_SWAPSIZE=512
```

스왑파일 서비스를 재시작하기 전에:

```
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start
```

### Raspberry Pi 2

Raspberry Pi 2에서 사용되는 ARM CPU 유형은 LLVM에서 감지되지 않습니다. 다음을 `Make.user`에 추가하여 CPU 대상을 명시적으로 설정하십시오:

`JULIA_CPU_TARGET=cortex-a7`

정확한 컴파일러와 배포판에 따라 지원되지 않는 인라인 어셈블리로 인해 빌드 실패가 발생할 수 있습니다. 그런 경우 `Make.user`에 `MCPU=armv7-a`를 추가하세요.

## AArch64 (ARMv8)

줄리아는 ARMv8 CPU에서 작업하고 빌드할 것으로 예상됩니다. 일반적으로 [build instructions](https://github.com/JuliaLang/julia/blob/master/README.md)를 따라야 합니다. 줄리아는 스스로 빌드하기 위해 약 8GB의 RAM 또는 스왑이 활성화되어 있기를 기대합니다.

### Known issues

Julia v1.10부터 [JITLink](https://llvm.org/docs/JITLink.html)는 LLVM 15 이상 버전과 연결할 때 모든 운영 체제에서 이 아키텍처에 대해 자동으로 활성화됩니다. [bug in LLVM memory manager](https://github.com/llvm/llvm-project/issues/63236)로 인해 비트리비얼 워크로드는 리눅스에서 메모리 매핑의 한도(`mmap`)를 초과할 수 있는 너무 많은 메모리 매핑을 생성할 수 있으며, 이로 인해 다음과 같은 오류가 발생할 수 있습니다.

```
JIT session error: Cannot allocate memory
```

이런 일이 발생하면 시스템 관리자에게 메모리 매핑의 한도를 늘려달라고 요청하세요. 예를 들어 다음 명령어를 사용하여 조정할 수 있습니다.

```
sysctl -w vm.max_map_count=262144
```
