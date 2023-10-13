# 構築手順

## 初期化(package.json が作成される)

```bash
# 初期化
$ pnpm init
```

## monorepo(ディレクトリ)を定義

pnpm-workspace.yaml

```yaml
packages:
  - "packages/*"
```

## ルートディレクトリから各アプリのスクリプトを実行

package.json

```json
{
  "name": "pnpm-monorepo-test",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "app1": "pnpm -F \"app1\"",
    "app2": "pnpm -F \"app2\""
  },
  "keywords": [],
  "author": "yoshi0518",
  "license": "ISC"
}
```

packages/app1/package.json

```json
{
  "name": "app1",
  "scripts": {
    "test": "echo \"hello app1!\""
  }
}
```

packages/app2/package.json

```json
{
  "name": "app2",
  "scripts": {
    "test": "echo \"hello app2!\""
  }
}
```

```bash
$ pnpm app1 test
$ pnpm app2 test
```

# Node モジュールをインストール

packages/app1/node_modules はシンボリックリンクが作成され、モジュールの実体は root の node_modules に保管される。

```bash
$ cd packages/app1
$ pnpm add axios
```
