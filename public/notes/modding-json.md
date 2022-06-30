---
aliases: ['Minecraft Modding Jsonを扱う方法']
tags: []
datetime-created: '2022-06-30 21:56'
---

# Minecraft Modding Jsonを扱う方法
- MinecraftではGsonが使用されている
- 普通にGsonが使える
- オブジェクトのクラスを作ってGson.fromJson(string, class)でパースできる
	- すべてのフィールドを作る必要はない（必要なやつだけでいい）