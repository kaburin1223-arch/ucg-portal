# UCG Portal GitHub Pages パッケージ

## 構成

```text
repo-root/
├─ .nojekyll
├─ README.md
├─ index.html
├─ builder/
│  └─ index.html
└─ records/
   └─ index.html
```

- `index.html` : ポータル
- `builder/index.html` : デッキビルダー＆シミュレータ
- `records/index.html` : 戦績記録ツール
- `.nojekyll` : GitHub Pages で静的ファイルをそのまま配信するための保険

## 公開の考え方

この構成は、同一リポジトリ配下で GitHub Pages に公開し、同一オリジンの `localStorage` を共有する前提です。
そのため、以下のような URL になります。

```text
https://<user>.github.io/<repo>/
https://<user>.github.io/<repo>/builder/
https://<user>.github.io/<repo>/records/
```

## 推奨手順

1. GitHub に新規リポジトリを作成する
2. このフォルダ内のファイルをそのまま配置して push する
3. GitHub の `Settings` → `Pages` を開く
4. `Build and deployment` の `Source` で `Deploy from a branch` を選ぶ
5. `Branch` は `main`、`Folder` は `/ (root)` を選ぶ
6. 保存後、公開 URL が発行される

## 既存データ運用

1. まず既存のローカルバックアップを手元に残す
2. Pages 公開後、ポータルを開く
3. `既存データを同期` を実行する
4. builder / records をそれぞれ開いて表示を確認する
5. 問題なければポータルから `全体バックアップ出力` を行う

## カスタムドメインを使う場合

- GitHub Pages 側でカスタムドメインを設定
- ドメイン管理側で必要な DNS レコードを設定
- HTTPS が有効になるまで少し待つ

## 注意

- `builder` と `records` を別リポジトリに分けると、オリジンが変わり `localStorage` 共有が難しくなります
- そのため、最初は必ず **1 リポジトリ配下** で運用してください
