```
zip_test_entry(x::ZipReader, i::Integer)::Nothing
```

エントリ `i` に問題がある場合、エラーが発生します。そうでなければ、何も返しません。

これにより、エントリが読み込まれ、crc32が一致するかどうかも確認されます。
