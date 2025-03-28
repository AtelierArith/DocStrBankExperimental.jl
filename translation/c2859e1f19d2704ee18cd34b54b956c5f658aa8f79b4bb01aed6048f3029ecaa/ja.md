```
finalizer(f, x)
```

関数 `f(x)` を登録し、`x` へのプログラムからアクセス可能な参照がなくなったときに呼び出され、`x` を返します。`x` の型は `mutable struct` でなければならず、そうでない場合は関数がエラーをスローします。

`f` はタスクスイッチを引き起こしてはいけません。これにより、`println` のようなほとんどの I/O 操作が除外されます。デバッグ目的で、`@async` マクロを使用して（ファイナライザの外でコンテキストスイッチを遅延させるため）たり、C の I/O 関数を直接呼び出すために `ccall` を使用することが役立つ場合があります。

`f` の実行に対して保証されたワールドエイジはありません。ファイナライザが登録されたワールドエイジまたはそれ以降のワールドエイジで呼び出される可能性があります。

# 例

```julia
finalizer(my_mutable_struct) do x
    @async println("Finalizing $x.")
end

finalizer(my_mutable_struct) do x
    ccall(:jl_safe_printf, Cvoid, (Cstring, Cstring), "Finalizing %s.", repr(x))
end
```

ファイナライザはオブジェクトの構築時に登録できます。以下の例では、ファイナライザが新しく作成されたミュータブル構造体 `x` を返すことに暗黙的に依存していることに注意してください。

```julia
mutable struct MyMutableStruct
    bar
    function MyMutableStruct(bar)
        x = new(bar)
        f(t) = @async println("Finalizing $t.")
        finalizer(f, x)
    end
end
```
