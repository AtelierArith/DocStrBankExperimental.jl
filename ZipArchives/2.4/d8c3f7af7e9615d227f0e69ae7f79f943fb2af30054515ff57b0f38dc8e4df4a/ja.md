```
zip_test(r::ZipReader)::Nothing
```

アーカイブ内のすべてのエントリを `1` から `zip_nentries(r)` までの順序でテストします。最初の無効なエントリに対してエラーをスローします。
