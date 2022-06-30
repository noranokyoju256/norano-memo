---
aliases: ['Minecraft Modding']
tags: []
datetime-created: '2022-06-21 22:33'
---
# Minecraft Modding
- [Minecraft Modding Jsonを扱う方法](modding-json.md)
## 環境構築
- ForgeからMdkをインストールしてきて解凍
- 適当な位置にフォルダをコピー
- IntelliJで開く
- 右のGradleからReload All Gradle Projectsを実行
- Tasks/forgegradle runs/genIntelliJRunsを実行
- 実行構成をRunClientに変更

## ビルド方法
- プロジェクトフォルダでコマンドプロンプトを開いて`.\gradlew.bat build`を実行
- 参考
	- [[Java]MinecraftのModを作成しよう 1.14.4【99. Modの出力】 - Qiita](https://qiita.com/koteko/items/cbcfe448def02c3413b9)