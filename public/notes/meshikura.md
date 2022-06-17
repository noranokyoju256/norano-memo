---
aliases: ['メシを食うたび強くなるマインクラフト']
tags: ['meshikura']
datetime-created: '2022-06-10 17:27'
---

# メシを食うたび強くなるマインクラフト
- [meshikura-mods](meshikura-mods.md)
- [meshikura-foods](meshikura-foods.md)
- 
## ToDo
- [ ] うぷ主の立ち絵
- [ ] マイクラのスキン
- [ ] Mod選定
- [ ] バックアップ機構
- [ ] YT Follower Counter

## テストプレイ　メモ
- 食事シーンはまとめたほうがいいかも
- 一度に10種類（ハート1個分）食べるように
- 1パートやること1つ
- 序盤に作れる料理

```

#List of diet effects
[[effects]]

	[[effects.status_effects]]
		name = "minecraft:regeneration"
		power = 0

	[[effects.conditions]]
		groups = ["proteins", "fruits", "vegetables", "grains"]
		match = "all"
		above = 0.8
		below = 1.0

[[effects]]

	[[effects.attributes]]
		name = "minecraft:generic.attack_damage"
		operation = "add"
		amount = 3.0

	[[effects.conditions]]
		groups = ["proteins"]
		match = "all"
		above = 0.8
		below = 1.0

[[effects]]

	[[effects.attributes]]
		name = "minecraft:generic.movement_speed"
		operation = "multiply_base"
		amount = 0.3

	[[effects.status_effects]]
		name = "minecraft:jump_boost"
		power = 1

	[[effects.conditions]]
		groups = ["fruits"]
		match = "all"
		above = 0.8
		below = 1.0

[[effects]]

	[[effects.status_effects]]
		name = "minecraft:resistance"
		power = 0

	[[effects.conditions]]
		groups = ["vegetables"]
		match = "all"
		above = 0.8
		below = 1.0

[[effects]]

	[[effects.status_effects]]
		name = "minecraft:haste"
		power = 0

	[[effects.attributes]]
		name = "minecraft:generic.attack_speed"
		operation = "multiply_base"
		amount = 0.3

	[[effects.conditions]]
		groups = ["grains"]
		match = "all"
		above = 0.8
		below = 1.0


```

```

[milestones]
	#Number of hearts you start out with.
	#Range: 0 ~ 1000
	baseHearts = 1
	#Number of hearts you gain for reaching a new milestone.
	#Range: 0 ~ 1000
	heartsPerMilestone = 1
	#A list of numbers of unique foods you need to eat to unlock each milestone, in ascending order. Naturally, adding more milestones lets you earn more hearts.
	milestones = [5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100
	, 105, 110, 115, 120, 125, 130, 135, 140, 145, 150, 155, 160, 165, 170, 175, 180, 185, 190, 195, 200]

[filtering]
	#Foods in this list won't affect the player's health nor show up in the food book.
	blacklist = []
	#When this list contains anything, the blacklist is ignored and instead only foods from here count.
	whitelist = []
	#The minimum hunger value foods need to provide in order to count for milestones, in half drumsticks.
	#Range: 0 ~ 1000
	minimumFoodValue = 1

[miscellaneous]
	#Whether or not to reset the food list on death, effectively losing all bonus hearts.
	resetOnDeath = false
	#If true, eating foods outside of survival mode (e.g. creative/adventure) is not tracked and thus does not contribute towards progression.
	limitProgressionToSurvival = false


```