```
@ccall library.function_name(argvalue1::argtype1, ...)::returntype
@ccall function_name(argvalue1::argtype1, ...)::returntype
@ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

在 C 导出的共享库中调用一个函数，由 `library.function_name` 指定，其中 `library` 是一个字符串常量或字面量。可以省略库名，在这种情况下，`function_name` 在当前进程中解析。或者，`@ccall` 也可以用于调用一个函数指针 `$function_pointer`，例如由 `dlsym` 返回的指针。

每个传递给 `@ccall` 的 `argvalue` 都会通过自动插入调用 `unsafe_convert(argtype, cconvert(argtype, argvalue))` 转换为相应的 `argtype`。（有关详细信息，请参见 [`unsafe_convert`](@ref Base.unsafe_convert) 和 [`cconvert`](@ref Base.cconvert) 的文档。）在大多数情况下，这仅仅导致调用 `convert(argtype, argvalue)`。

# 示例

```
@ccall strlen(s::Cstring)::Csize_t
```

这调用 C 标准库函数：

```
size_t strlen(char *)
```

使用名为 `s` 的 Julia 变量。另请参见 `ccall`。

支持可变参数，使用以下约定：

```
@ccall printf("%s = %d"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
```

分号用于将必需参数（至少必须有一个）与可变参数分开。

使用外部库的示例：

```
# g_uri_escape_string 的 C 签名：
# char *g_uri_escape_string(const char *unescaped, const char *reserved_chars_allowed, gboolean allow_utf8);

const glib = "libglib-2.0"
@ccall glib.g_uri_escape_string(my_uri::Cstring, ":/"::Cstring, true::Cint)::Cstring
```

如果需要，字符串字面量也可以直接在函数名之前使用，例如 `"libglib-2.0".g_uri_escape_string(...`
