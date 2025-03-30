# macOS

현재 Xcode 명령줄 도구가 설치되어 있어야 합니다: 터미널에서 `xcode-select --install`을 실행하세요. macOS 업데이트 후에는 이 터미널 명령을 다시 실행해야 하며, 그렇지 않으면 누락된 라이브러리나 헤더와 관련된 오류가 발생할 수 있습니다.

종속 라이브러리는 이제 [BinaryBuilder](https://binarybuilder.org)로 빌드되며 자동으로 다운로드됩니다. 이것은 Julia 소스를 빌드하는 선호되는 방법입니다. 모든 라이브러리를 직접 빌드하려는 경우, Julia 종속성을 컴파일하기 위해 64비트 gfortran이 필요합니다.

```bash
brew install gcc
```

`LD_LIBRARY_PATH` 또는 `DYLD_LIBRARY_PATH`를 `.bashrc` 또는 이에 상응하는 파일에 설정한 경우, Julia가 함께 제공되는 다양한 라이브러리를 찾지 못할 수 있습니다. Julia가 작동하려면 이러한 환경 변수를 해제해야 합니다.
