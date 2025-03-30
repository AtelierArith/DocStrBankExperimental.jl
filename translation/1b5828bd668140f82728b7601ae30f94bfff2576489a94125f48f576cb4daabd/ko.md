# Handling Operating System Variation

크로스 플랫폼 애플리케이션이나 라이브러리를 작성할 때, 운영 체제 간의 차이를 허용하는 것이 종종 필요합니다. 변수 `Sys.KERNEL`은 이러한 경우를 처리하는 데 사용할 수 있습니다. `Sys` 모듈에는 이를 더 쉽게 만들기 위해 의도된 여러 함수가 있으며, 예를 들어 `isunix`, `islinux`, `isapple`, `isbsd`, `isfreebsd`, `iswindows`가 있습니다. 이들은 다음과 같이 사용할 수 있습니다:

```julia
if Sys.iswindows()
    windows_specific_thing(a)
end
```

`islinux`, `isapple`, `isfreebsd`는 `isunix`의 상호 배타적인 하위 집합임을 유의하십시오. 또한, 다음 예제에서 보여주듯이 유효하지 않은 코드를 조건부로 숨기는 데 사용할 수 있는 매크로 `@static`이 있습니다.

간단한 블록:

```
ccall((@static Sys.iswindows() ? :_fopen : :fopen), ...)
```

복잡한 블록:

```julia
@static if Sys.islinux()
    linux_specific_thing(a)
elseif Sys.isapple()
    apple_specific_thing(a)
else
    generic_thing(a)
end
```

조건문을 중첩할 때, `@static`은 각 레벨마다 반복되어야 합니다(괄호는 선택 사항이지만 가독성을 위해 권장됩니다):

```julia
@static Sys.iswindows() ? :a : (@static Sys.isapple() ? :b : :c)
```
