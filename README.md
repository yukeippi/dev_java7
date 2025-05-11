# Java 7 サンプルプロジェクト

このリポジトリはJava 7を使用したシンプルなサンプルプロジェクトです。Maven構成が含まれており、すぐに開発を始めることができます。

## 環境構成

- Java 7 (OpenJDK 7)
- Maven 3.x（Maven Wrapper経由でも実行可能）

## プロジェクト概要

このプロジェクトは、Java 7環境での基本的な開発構成を示すサンプルです。シンプルな「Hello World」アプリケーションが含まれています。

## 使用方法

### Mavenでのビルドと実行

```bash
# Mavenがインストールされている場合
mvn clean package
java -jar target/java7-docker-demo-1.0-SNAPSHOT.jar

# または、Maven Wrapperを使用する場合
./mvnw clean package
java -jar target/java7-docker-demo-1.0-SNAPSHOT.jar
```

実行すると、「Hello, Java 7 Docker World!」というメッセージが表示されます。

## プロジェクト構造

```
.
├── src/                 # ソースコード
│   └── main/
│       └── java/
│           └── com/
│               └── example/
│                   └── HelloWorld.java  # サンプルJavaアプリケーション
├── mvnw               # Maven Wrapper実行スクリプト
├── pom.xml            # Mavenプロジェクト設定
└── settings.xml       # Maven追加設定（オフラインモード、JBossリポジトリミラー）
```

## Maven設定の詳細

### pom.xml

- Java 7のコンパイル設定
- JUnit 4.12のテスト依存関係
- メインクラス: `com.example.HelloWorld`

### settings.xml

- ローカルリポジトリの設定
- オフラインモードの有効化
- JBossパブリックリポジトリをMavenセントラルのミラーとして設定

### Maven Wrapper (mvnw)

- Mavenがインストールされていない環境でもプロジェクトをビルド可能
- Java 7向けにTLS 1.2サポートを追加する設定を含む

## サンプルコード

`HelloWorld.java`は単純な「Hello World」プログラムで、コンソールに「Hello, Java 7 Docker World!」というメッセージを出力します。

```java
package com.example;

/**
 * シンプルなHello Worldプログラム
 */
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java 7 Docker World!");
    }
}
```

## トラブルシューティング

### ビルド関連の問題

- **エラー**: Mavenビルドに失敗する
  - **解決策**: `settings.xml`の設定を確認し、必要に応じてオフラインモードを無効にしてください
  - JBossリポジトリへの接続が可能か確認してください

- **エラー**: Java関連のエラーが発生する
  - **解決策**: `JAVA_HOME`環境変数が正しく設定されていることを確認してください
  - Java 7がインストールされていることを確認してください

## ライセンス

このプロジェクトはApache License 2.0の下で公開されています。
