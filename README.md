# Java 7 サンプルプロジェクト

このリポジトリはJava 7を使用したシンプルなサンプルプロジェクトです。基本的なJavaプログラムの構成を示しています。

## 環境構成

- Java 7 (OpenJDK 7)

## プロジェクト概要

このプロジェクトは、Java 7環境での基本的な開発構成を示すサンプルです。シンプルな「Hello World」アプリケーションが含まれています。

## 使用方法

### コンパイルと実行

```bash
# コンパイル
javac -encoding UTF-8 -d classes src/com/example/HelloWorld.java

# 実行
java -cp classes com.example.HelloWorld
```

実行すると、「Hello, Java 7 Docker World!」というメッセージが表示されます。

## プロジェクト構造

```
.
├── README.md           # このファイル
└── src/                # ソースコード
    └── com/
        └── example/
            ├── HelloWorld.class  # コンパイル済みのクラスファイル
            └── HelloWorld.java   # サンプルJavaアプリケーション
```

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

### コンパイル・実行関連の問題

- **エラー**: Javaコンパイルに失敗する
  - **解決策**: `JAVA_HOME`環境変数が正しく設定されていることを確認してください
  - Java 7がインストールされていることを確認してください
  - `javac -version`コマンドでJavaコンパイラのバージョンを確認してください

- **エラー**: クラスが見つからないエラーが発生する
  - **解決策**: パッケージ構造（com.example）に合わせてクラスパスが正しく設定されていることを確認してください

## ライセンス

このプロジェクトはApache License 2.0の下で公開されています。
