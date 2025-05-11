# Java 7 開発環境

このリポジトリはJava 7アプリケーション開発用の環境を提供します。VS Code DevContainerを使用して、Windows環境で一貫した開発環境を簡単にセットアップできます。

## 環境構成

- Java 7 (OpenJDK)
- Maven 3.2.5
- Debian Bullseye ベースのコンテナ

## 前提条件

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop/)
- VS Codeの[Dev Containers拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- WSL2が有効化されていること（Windows 10/11）

## Windows環境での使用方法

1. **Docker Desktopの設定**
   - Docker Desktopが最新バージョンであることを確認してください
   - WSL2統合が有効になっていることを確認してください

2. **devcontainer.jsonの設定**
   - `.devcontainer/devcontainer.json`ファイルでは、Linux/AMD64プラットフォームを指定しています
   - この設定はWindows環境で適切に動作するために必要です

## 使用方法

1. このリポジトリをクローンします
2. VS Codeでフォルダを開きます
3. VS Codeが「Reopen in Container」を提案するポップアップを表示したら、それをクリックします
   - または、コマンドパレット（F1キー）を開き、「Dev Containers: Reopen in Container」を選択します
4. コンテナのビルドと起動が完了するまで待ちます

## トラブルシューティング

### Windows環境での問題

- **エラー**: WSL2関連のエラーが発生する場合
  - **解決策**: WSL2が正しくインストールされ、有効化されていることを確認してください
  - [WSL2のインストールガイド](https://docs.microsoft.com/ja-jp/windows/wsl/install)を参照してください

- **エラー**: Dockerコンテナの起動に失敗する
  - **解決策**: Docker Desktopが実行中であることを確認し、必要に応じてDocker Desktopを再起動してください
  - Windowsセキュリティ設定やファイアウォールが原因の場合もあります

### 一般的な問題

- **エラー**: コンテナのビルドに失敗する
  - **解決策**: Docker Desktopのリソース設定（メモリ、CPU）を確認し、必要に応じて増やしてください

- **エラー**: Javaコマンドが見つからない
  - **解決策**: コンテナ内で`echo $JAVA_HOME`を実行して、Java環境が正しく設定されていることを確認してください

## プロジェクト構造

```
.
├── .devcontainer/       # DevContainer設定
│   ├── devcontainer.json
│   └── Dockerfile
├── src/                 # ソースコード
│   └── main/
│       └── java/
│           └── com/
│               └── example/
│                   └── HelloWorld.java
└── pom.xml             # Mavenプロジェクト設定
```

## ライセンス

このプロジェクトはMITライセンスの下で公開されています。
