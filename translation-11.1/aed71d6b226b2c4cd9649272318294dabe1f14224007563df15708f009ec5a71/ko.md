# Memory layout of Julia Objects

## Object layout (`jl_value_t`)

`jl_value_t` 구조체는 Julia 가비지 컬렉터가 소유하는 메모리 블록의 이름으로, 메모리 내의 Julia 객체와 관련된 데이터를 나타냅니다. 타입 정보가 없으면, 이는 단순히 불투명 포인터입니다:

```c
typedef struct jl_value_t* jl_pvalue_t;
```

각 `jl_value_t` 구조체는 Julia 객체에 대한 메타데이터 정보(예: 유형 및 가비지 컬렉터(gc) 도달 가능성)를 포함하는 `jl_typetag_t` 구조체에 포함되어 있습니다:

```c
typedef struct {
    opaque metadata;
    jl_value_t value;
} jl_typetag_t;
```

모든 Julia 객체의 유형은 리프 `jl_datatype_t` 객체의 인스턴스입니다. `jl_typeof()` 함수는 이를 조회하는 데 사용할 수 있습니다:

```c
jl_value_t *jl_typeof(jl_value_t *v);
```

객체의 레이아웃은 그 유형에 따라 다릅니다. 반사 메서드를 사용하여 해당 레이아웃을 검사할 수 있습니다. 필드는 get-field 메서드 중 하나를 호출하여 접근할 수 있습니다:

```c
jl_value_t *jl_get_nth_field_checked(jl_value_t *v, size_t i);
jl_value_t *jl_get_field(jl_value_t *o, char *fld);
```

필드 유형이 사전에 모두 포인터로 알려져 있다면, 값은 배열 접근으로 직접 추출할 수도 있습니다:

```c
jl_value_t *v = value->fieldptr[n];
```

예를 들어, "박스된" `uint16_t`는 다음과 같이 저장됩니다:

```c
struct {
    opaque metadata;
    struct {
        uint16_t data;        // -- 2 bytes
    } jl_value_t;
};
```

이 객체는 `jl_box_uint16()`에 의해 생성됩니다. `jl_value_t` 포인터는 구조체의 상단에 있는 메타데이터가 아니라 데이터 부분을 참조한다는 점에 유의하세요.

값은 많은 상황에서 "언박스"되어 저장될 수 있습니다(메타데이터 없이 데이터만 저장되며, 아예 저장되지 않고 레지스터에만 유지될 수도 있음), 따라서 박스의 주소가 고유 식별자라고 가정하는 것은 안전하지 않습니다. 대신 두 개의 알 수 없는 객체의 동등성을 비교하기 위해 "egal" 테스트(줄리아의 `===` 함수에 해당)를 사용해야 합니다:

```c
int jl_egal(jl_value_t *a, jl_value_t *b);
```

이 최적화는 API에 상대적으로 투명해야 하며, `jl_value_t` 포인터가 필요할 때마다 객체가 필요에 따라 "박스" 처리될 것입니다.

`jl_value_t` 포인터의 메모리 수정은 객체가 변경 가능할 경우에만 허용됩니다. 그렇지 않으면 값의 수정이 프로그램을 손상시킬 수 있으며 결과는 정의되지 않습니다. 값의 변경 가능성 속성은 다음과 같이 쿼리할 수 있습니다:

```c
int jl_is_mutable(jl_value_t *v);
```

저장되는 객체가 `jl_value_t`인 경우, 줄리아 가비지 컬렉터에도 알림을 보내야 합니다:

```c
void jl_gc_wb(jl_value_t *parent, jl_value_t *ptr);
```

그러나 매뉴얼의 [Embedding Julia](@ref) 섹션은 다양한 유형의 박싱 및 언박싱에 대한 다른 세부 사항을 다루고 가비지 컬렉션 상호작용을 이해하기 위해 이 시점에서 필수적으로 읽어야 합니다.

미러 구조체는 일부 내장 타입에 대해 [defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h)입니다. 해당하는 전역 `jl_datatype_t` 객체는 [`jl_init_types` in `jltypes.c`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c)에 의해 생성됩니다.

## Garbage collector mark bits

가비지 수집기는 `jl_typetag_t`의 메타데이터 부분에서 여러 비트를 사용하여 시스템의 각 객체를 추적합니다. 이 알고리즘에 대한 자세한 내용은 [garbage collector implementation in `gc.c`](https://github.com/JuliaLang/julia/blob/master/src/gc.c)의 주석에서 확인할 수 있습니다.

## Object allocation

대부분의 새로운 객체는 `jl_new_structv()`에 의해 할당됩니다:

```c
jl_value_t *jl_new_struct(jl_datatype_t *type, ...);
jl_value_t *jl_new_structv(jl_datatype_t *type, jl_value_t **args, uint32_t na);
```

비록, [`isbits`](@ref) 객체는 메모리에서 직접 생성될 수도 있습니다:

```c
jl_value_t *jl_new_bits(jl_value_t *bt, void *data)
```

일부 객체는 위의 함수 대신 사용해야 하는 특별한 생성자를 가지고 있습니다:

유형:

```c
jl_datatype_t *jl_apply_type(jl_datatype_t *tc, jl_tuple_t *params);
jl_datatype_t *jl_apply_array_type(jl_datatype_t *type, size_t dim);
```

이러한 옵션들이 가장 일반적으로 사용되지만, 더 많은 저수준 생성자도 있으며, 이는 [`julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h)에 선언되어 있습니다. 이들은 `jl_init_types()`에서 사용되어 줄리아 시스템 이미지를 부트스트랩하는 데 필요한 초기 유형을 생성합니다.

튜플:

```c
jl_tuple_t *jl_tuple(size_t n, ...);
jl_tuple_t *jl_tuplev(size_t n, jl_value_t **v);
jl_tuple_t *jl_alloc_tuple(size_t n);
```

튜플의 표현은 줄리아 객체 표현 생태계에서 매우 독특합니다. 경우에 따라 [`Base.tuple()`](@ref) 객체는 튜플에 포함된 객체에 대한 포인터 배열일 수 있습니다.

```c
typedef struct {
    size_t length;
    jl_value_t *data[length];
} jl_tuple_t;
```

그러나 다른 경우에는 튜플이 익명 [`isbits`](@ref) 유형으로 변환되어 언박스된 상태로 저장되거나, (만약 `jl_value_t*`로서 일반적인 맥락에서 사용되지 않는다면) 아예 저장되지 않을 수 있습니다.

기호:

```c
jl_sym_t *jl_symbol(const char *str);
```

함수 및 메서드 인스턴스:

```c
jl_function_t *jl_new_generic_function(jl_sym_t *name);
jl_method_instance_t *jl_new_method_instance(jl_value_t *ast, jl_tuple_t *sparams);
```

배열:

```c
jl_array_t *jl_new_array(jl_value_t *atype, jl_tuple_t *dims);
jl_array_t *jl_alloc_array_1d(jl_value_t *atype, size_t nr);
jl_array_t *jl_alloc_array_nd(jl_value_t *atype, size_t *dims, size_t ndims);
```

다음의 많은 것들이 다양한 특별 목적을 위한 대체 할당 함수를 가지고 있다는 점에 유의하십시오. 여기의 목록은 더 일반적인 용도를 반영하지만, 더 완전한 목록은 [`julia.h` header file](https://github.com/JuliaLang/julia/blob/master/src/julia.h)를 읽음으로써 찾을 수 있습니다.

내부적으로 Julia에서는 저장소가 일반적으로 `newstruct()` (특수 유형의 경우 `newobj()`)에 의해 할당됩니다:

```c
jl_value_t *newstruct(jl_value_t *type);
jl_value_t *newobj(jl_value_t *type, size_t nfields);
```

가장 낮은 수준에서 메모리는 가비지 컬렉터(`gc.c`)에 대한 호출로 할당되며, 그 후 유형으로 태그가 지정됩니다:

```c
jl_value_t *jl_gc_allocobj(size_t nbytes);
void jl_set_typeof(jl_value_t *v, jl_datatype_t *type);
```

!!! note "Out of date Warning"
    `jl_gc_allocobj` 함수에 대한 문서 및 사용법이 오래되었을 수 있습니다.


모든 객체는 4바이트의 배수로 할당되며 플랫폼 포인터 크기에 맞춰 정렬됩니다. 메모리는 작은 객체의 경우 풀에서 할당되거나, 큰 객체의 경우 `malloc()`을 사용하여 직접 할당됩니다.

!!! sidebar "Singleton Types"
    싱글턴 타입은 인스턴스가 하나만 존재하며 데이터 필드가 없습니다. 싱글턴 인스턴스는 크기가 0바이트이며, 메타데이터만으로 구성됩니다. 예: `nothing::Nothing`.

    [Singleton Types](@ref man-singleton-types)와 [Nothingness and missing values](@ref)를 참조하세요.

