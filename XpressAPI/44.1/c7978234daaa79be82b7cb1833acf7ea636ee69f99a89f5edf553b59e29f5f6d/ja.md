```
XPRS_ERRORCODE
```

最も最近発生したオプティマイザのエラー番号です。（整数）

これは、オプティマイザ関数が非ゼロの値を返すことによってエラーを示した後に、発生した正確なエラーまたは警告を特定するのに役立ちます。返り値自体はエラー番号ではありません。可能なエラー番号のリスト、それらが示すエラーや警告、そしてそれらの意味や解決方法に関するアドバイスについては、セクションを参照してください。短いエラーメッセージはXPRSgetlasterrorを使用して取得でき、すべてのメッセージはユーザー出力コールバック関数を使用してインターセプトできます。詳細はXPRSaddcbmessageを参照してください。
