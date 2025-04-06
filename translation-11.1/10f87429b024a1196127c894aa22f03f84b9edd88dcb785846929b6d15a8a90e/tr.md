# Calling Conventions

Julia, dört farklı amaç için üç çağrı konvansiyonu kullanır:

| Name    | Prefix    | Purpose                          |
|:------- |:--------- |:-------------------------------- |
| Native  | `julia_`  | Speed via specialized signatures |
| JL Call | `jlcall_` | Wrapper for generic calls        |
| JL Call | `jl_`     | Builtins                         |
| C ABI   | `jlcapi_` | Wrapper callable from C          |

## Julia Native Calling Convention

Yerel çağrı sözleşmesi, hızlı genel olmayan çağrılar için tasarlanmıştır. Genellikle özel bir imza kullanır.

  * LLVM hayaletleri (sıfır uzunlukta türler) atlanmıştır.
  * LLVM skalarları ve vektörleri değer olarak geçirilir.
  * LLVM toplulukları (diziler ve yapılar) referansla geçilir.

Küçük dönüş değerleri LLVM dönüş değerleri olarak döndürülür. Büyük dönüş değerleri, çağıranın bir dönüş alanına işaretçi sağladığı "yapı dönüşü" (`sret`) kuralı aracılığıyla döndürülür.

Bir argüman veya dönen değerler, homojen bir demet olarak, bazen bir LLVM dizisi yerine bir LLVM vektörü olarak temsil edilir.

## JL Call Convention

JL Çağrı konvansiyonu, yerleşik işlevler ve genel dağıtım için kullanılır. Bu konvansiyonu kullanan elle yazılmış işlevler `JL_CALLABLE` makrosu ile bildirilir. Konvansiyon tam olarak 3 parametre kullanır:

  * `F`  - Uygulanan fonksiyonun Julia temsili
  * `args` - kutuya işaret eden işaretçiler dizisi
  * `nargs` - dizinin uzunluğu

Dönüş değeri bir kutuya işaret eden bir işaretçidir.

## C ABI

C ABI sarıcıları, C'den Julia'yı çağırmayı sağlar. Sarıcı, bir işlevi yerel çağrı sözleşmesini kullanarak çağırır.

Tuplelar her zaman C dizileri olarak temsil edilir.
