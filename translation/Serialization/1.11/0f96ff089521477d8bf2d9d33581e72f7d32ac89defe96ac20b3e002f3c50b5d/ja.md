```
Serialization.writeheader(s::AbstractSerializer)
```

指定されたシリアライザーに識別ヘッダーを書き込みます。ヘッダーは次のように8バイトで構成されています：

| オフセット | 説明                                      |
|:----- |:--------------------------------------- |
| 0     | タグバイト (0x37)                            |
| 1-2   | シグネチャバイト "JL"                           |
| 3     | プロトコルバージョン                              |
| 4     | ビット 0-1: エンディアン: 0 = リトル, 1 = ビッグ       |
| 4     | ビット 2-3: プラットフォーム: 0 = 32ビット, 1 = 64ビット |
| 5-7   | 予約済み                                    |
