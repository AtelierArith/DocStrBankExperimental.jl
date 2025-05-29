mPulse Query & Repository REST APIを使用して、テナントやアプリに関する情報を取得します。

[![GH Build](https://github.com/akamai/mPulseAPI.jl/workflows/CI/badge.svg)](https://github.com/akamai/mPulseAPI.jl/actions/workflows/CI.yml?query=branch%3Amain) [![Coverage Status](https://coveralls.io/repos/github/akamai/mPulseAPI.jl/badge.svg?branch=main)](https://coveralls.io/github/akamai/mPulseAPI.jl?branch=main) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://akamai.github.io/mPulseAPI.jl/)

## ドキュメント

### このモジュール:

  * mPulseAPI.jl: [https://akamai.github.io/mPulseAPI.jl/](https://akamai.github.io/mPulseAPI.jl/)

### このモジュールが使用するREST API:

  * mPulse API: [https://techdocs.akamai.com/mpulse/reference/api](https://techdocs.akamai.com/mpulse/reference/api)

## 簡単な使用法

このスニペットを使用すると、すぐに動作を開始できます。詳細については、完全なドキュメントを参照してください。

`apiToken`に関する詳細は[APIトークンの生成方法](apiToken.md)を参照してください。

```julia
using mPulseAPI

# mPulseは認証のためにapiTokenを使用します
token = getRepositoryToken("<tenant name>", "<mPulse api token for tenant>")


# アプリ名からドメインを取得
domain = getRepositoryDomain(token, appName="<app name from mPulse>")

# App Key（以前のAPIキー）からドメインを取得
domain = getRepositoryDomain(token, appKey="<App Key from mPulse>")

domain["attributes"]["appKey"]                           # このアプリのApp Key（以前のAPIキー）を取得
                                                         # 
domain["custom_metrics"]                                 # カスタムメトリクスのDictを取得
domain["custom_metrics"]["Conversion Rate"]              # Conversion Rateカスタムメトリクスのマッピングを取得
domain["custom_metrics"]["Conversion Rate"]["fieldname"] # Conversion Rateカスタムメトリクスのフィールド名を取得
                                                         # 

# テナント内のすべてのドメインを取得
domains = getRepositoryDomain(token)


# テナントを取得
tenant = getRepositoryTenant(token, name="<tenant name from mPulse>")
```
