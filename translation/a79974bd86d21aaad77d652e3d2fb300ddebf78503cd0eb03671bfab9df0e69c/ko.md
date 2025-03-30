# FreeBSD

Clang은 FreeBSD 11.0-RELEASE 이상에서 기본 컴파일러입니다. 나머지 빌드 도구는 Ports Collection에서 사용할 수 있으며, `pkg install git gcc gmake cmake pkgconf`를 사용하여 설치할 수 있습니다. Julia를 빌드하려면 간단히 `gmake`를 실행하면 됩니다. (FreeBSD에서 `make`는 GNU Make가 아닌 호환되지 않는 BSD Make에 해당하므로 `gmake`를 사용해야 합니다.)

위에서 언급했듯이, `USE_SYSTEM_*` 플래그는 FreeBSD에서 주의해서 사용해야 한다는 점을 유의해야 합니다. 이는 많은 시스템 라이브러리와 Ports Collection의 라이브러리들이 시스템의 `libgcc_s.so.1`에 링크되거나, 시스템 `libgcc_s`에 링크되는 다른 라이브러리에 연결되기 때문입니다. 이 라이브러리는 자신의 GCC 버전을 4.6으로 선언하는데, 이는 Julia를 빌드하기에는 너무 오래된 버전이며, 링크할 때 다른 라이브러리와 충돌을 일으킬 수 있습니다. 따라서 Julia가 모든 종속성을 빌드하도록 허용하는 것이 강력히 권장됩니다. `USE_SYSTEM_*` 플래그를 사용하기로 선택한 경우, `/usr/local`이 기본적으로 컴파일러 경로에 포함되어 있지 않으므로, `Make.user`에 `LDFLAGS=-L/usr/local/lib`와 `CPPFLAGS=-I/usr/local/include`를 추가해야 할 수 있지만, 그렇게 하면 다른 종속성과 충돌할 수 있습니다.

x86 아키텍처는 컴파일러 런타임 라이브러리 지원 부족으로 인해 스레딩을 지원하지 않으므로, 32비트 시스템을 사용하는 경우 `Make.user`에서 `JULIA_THREADS=0`을 설정해야 할 수 있습니다.
