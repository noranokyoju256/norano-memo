---
aliases: ['Gitよく使うコマンド集']
tags: ['Git']
datetime-created: '2022-06-07 05:31'
---
# Gitよく使うコマンド集
- `git add .` 
	- ワーキングディレクトリのすべてのファイルをステージング
- `git reset HEAD <ファイル名>`
	- ステージングしたファイルを取り消し
- `git reset --soft HEAD^`
	- コミットを取り消し
- `git commit -m "message"`
	- メッセージを添えてコミット
- `git status`
	- ワーキングディレクトリの状態を確認する
- `git checkout -b <ブランチ名>`
	- 新たなブランチを作成し移動する
- `git merge <ブランチ名>`
	- マージする
- `git clone <url>`
	- リモートリポジトリからクローンする
- `git pull`
	- リモートリポジトリからプルする
- `git fetch`
	- リモートリポジトリからフェッチする

#### ローカルにリポジトリを作成しリモートにプッシュする
```
git init 
git add . 
git commit -m "Initial commit" 
git remote add origin <url> 
git push -u origin master
```
