# saori\_curl

## これは何？

curlを使って*UTF-8なテキストデータを返すURL*からテキストを取得するSAORIです。

## 使い方

```
Argument0: URL

Result: 取得に成功していたらOK、失敗していたら理由
ValueN: 帰ってきたデータを改行で分割した配列
```
## 使用ライブラリ

- libcurl

- 多分opensslとか色々
