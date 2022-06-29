---
aliases: ['メシクラ Config']
tags: []
datetime-created: '2022-06-29 13:08'
---

# メシクラ Config
## Diet
```toml
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

[[effects]]

	[[effects.attributes]]
		name = "minecraft:generic.movement_speed"
		operation = "multiply_base"
		amount = 0.25

	[[effects.status_effects]]
		name = "minecraft:hunger"
		power = 3

	[[effects.conditions]]
		groups = ["sugars"]
		match = "all"
		above = 0.8
		below = 1.0


```
## Spice of Life: Carrot Edition
```toml

[milestones]
	#Number of hearts you start out with.
	#Range: 0 ~ 1000
	baseHearts = 1
	#Number of hearts you gain for reaching a new milestone.
	#Range: 0 ~ 1000
	heartsPerMilestone = 1
	#A list of numbers of unique foods you need to eat to unlock each milestone, in ascending order. Naturally, adding more milestones lets you earn more hearts.
	milestones = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 150, 160, 170, 180, 190, 200]

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
## Improved Mobs
```toml

#With default value every difficulty perk maxes out at difficulty 250
[general]
	#Disable/Enables the whole difficulty scaling of this mod. Requires a mc restart
	"Enable difficulty scaling" = true
	#Time in ticks for which the difficulty shouldnt increase at the beginning. One full minecraft day is 24000 ticks
	#Range: > 0
	"Difficulty Delay" = 0
	#Handles increase in difficulty regarding current difficulty.
	#Format is <minimum current difficulty>-<increase every 2400 ticks>
	#Example ["0-0.01","10-0.1","30-0"]
	#So the difficulty increases by 0.01 every 2400 ticks (->0.1 per mc day) till it reaches a difficulty of 10.
	#Then it increases by 1 per mc day till it reaches 30 and then stops.
	"Difficulty Increase" = ["0-0.2", "100-0.1", "250-0"]
	#Wether difficulty should only increase with at least one online players or not
	"Ignore Players" = false
	#Should punish time skipping with e.g. bed, commands? If false, difficulty will increase by 0.1 regardless of skipped time.
	"Punish Time Skip" = true
	#Disable/Enable friendly fire for owned pets.
	FriendlyFire = false
	#Blacklist for pet you should't be able to give armor to. Pets from mods, which have custom armor should be included here.
	"Pet Blacklist" = []
	#Treat pet blacklist as whitelist
	"Pet Whitelist" = false
	#Increase difficulty with time
	#Here untill its back as a gamerule
	"Difficulty toggle" = true
	#How the difficulty at a position is calculated. Supported values are: 
	#GLOBAL: Serverwide difficulty value
	#PLAYERMAX: Maximum difficulty of players in a 256 radius around the position
	#PLAYERMEAN: Average difficulty of players in a 256 radius around the position
	#Allowed Values: GLOBAL, PLAYERMAX, PLAYERMEAN
	"Difficulty type" = "GLOBAL"

#Black/Whitelist for various stuff
[list]
	#Entities added here will be blacklisted from their assigned flags. Usage:
	#<entity registry name> or <namespace> followed by any of:
	#[ALL,ATTRIBUTES,ARMOR,HELDITEMS,BLOCKBREAK,USEITEM,LADDER,STEAL,GUARDIAN,PARROT,TARGETVILLAGER,NEUTRALAGGRO,REVERSE].
	#Having no flags is equal to ALL. Use REVERSE to reverse all flags. Some flags do nothing for certain mobs!
	#Examples:
	#minecraft:sheep is equal to minecraft:sheep|ALL and excludes sheeps from all modifications
	#minecraft:sheep|REVERSE|ATTRIBUTES will add sheep to attributes modification only
	#minecraft:sheep|ATTRIBUTES will add sheep to everything except attributes
	"More Entities" = ["minecraft:cod", "botania:doppleganger", "minecraft:donkey", "minecraft:squid", "minecraft:glow_squid", "minecraft:mule", "minecraft:skeleton_horse", "minecraft:strider", "minecraft:trader_llama", "minecraft:parrot", "minecraft:cow", "minecraft:zombie_horse", "minecraft:horse", "minecraft:bee", "minecraft:polar_bear", "minecraft:cat", "minecraft:pufferfish", "minecraft:bat", "minecraft:wandering_trader", "minecraft:salmon", "minecraft:fox", "minecraft:llama", "minecraft:pig", "minecraft:iron_golem", "minecraft:tropical_fish", "minecraft:turtle", "minecraft:sheep", "minecraft:snow_golem", "minecraft:mooshroom", "minecraft:villager", "minecraft:ocelot", "minecraft:goat", "botania:pixie", "minecraft:dolphin", "minecraft:chicken", "minecraft:wolf", "minecraft:panda", "minecraft:rabbit", "minecraft:axolotl"]
	#Any of the following 
	#[ATTRIBUTES, ARMOR, HELDITEMS, BLOCKBREAK, USEITEM, LADDER, STEAL, GUARDIAN, PARROT, TARGETVILLAGER, NEUTRALAGGRO]
	#added here will disable that feature.
	#E.g. ["GUARDIAN"] will disable the guardian feature
	"Flag Blacklist" = []
	#Treat ATTRIBUTES flags as whitelist
	"Attribute Whitelist" = false
	#Treat ARMOR flags as whitelist
	"Armor Equip Whitelist" = false
	#Treat HELDITEMS flags as whitelist
	"Held Equip Whitelist" = false
	#Treat BLOCKBREAK flags as whitelist
	"Breaker Whitelist" = false
	#Treat USEITEM flags as whitelist
	"Item Use Whitelist" = false
	#Treat LADDER flags as whitelist
	"Ladder Whitelist" = false
	#Treat STEAL flags as whitelist
	"Steal Whitelist" = false
	#Treat GUARDIAN flags as whitelist
	"Guardian Whitelist" = false
	#Treat PARROT flags as whitelist
	"Parrot Whitelist" = false
	#Treat TARGETVILLAGER flags as whitelist
	"Villager Whitelist" = false
	#Treat NEUTRALAGGRO flags as whitelist
	"Neutral Aggro Whitelist" = false

#Debugging
[debug]
	#Enable showing of entity paths
	"Path Debugging" = false

#Settings for mod integration
[integration]
	#Should the scaling health mods difficulty system be used instead of this ones. (Requires scaling health mod)
	"Use Scaling Health Mod" = true

#Settings regarding custom ai for mobs
[ai]
	#Whitelist for blocks, which can be actively broken. 
	#Usage: <registry name;classname;tag;namespace> put "!" infront to exclude blocks
	#Note: If you include common blocks (like grass blocks) the pathfinding will be a bit strange
	"Block Whitelist" = ["forge:glass", "forge:glass_panes", "minecraft:fence_gates", "forge:fence_gates", "minecraft:wooden_doors"]
	#Treat Block Whitelist as Blocklist
	"Block as Blacklist" = false
	#Use the block breaking sound instead of a knocking sound
	Sound = false
	#Chance for a mob to be able to break blocks
	#Range: 0.0 ~ 1.0
	"Breaker Chance" = 0.3
	#Initial cooldown for block breaking mobs
	#Range: > 0
	"Breaker Initial Cooldown" = 120
	#Cooldown for breaking blocks
	#Range: > 0
	"Breaker Cooldown" = 20
	#Chance for a mob to be able to steal items
	#Range: 0.0 ~ 1.0
	"Stealer Chance" = 0.3
	#Items which will be given to mobs who can break blocks. Empty list = no items. Syntax: id;weight
	"Breaking items" = ["minecraft:diamond_pickaxe;1", "minecraft:iron_axe;2"]
	#Should mobs be able to break tile entities? Evaluated before the break list
	"Break Tiles" = true
	#Chance for neutral mobs to be aggressive
	#Range: 0.0 ~ 1.0
	"Neutral Aggressive Chance" = 0.2
	#List for of pairs containing which mobs auto target others. Syntax is [mob id]-[mob id] where second value is the target.
	# e.g. minecraft:zombie-minecraft:skeleton makes all zombies target skeletons
	"Auto Target List" = []
	#Difficulty at which mobs are able to break blocks
	#Range: 0.0 ~ 1.7976931348623157E308
	"Difficulty Break AI" = 0.0
	#Difficulty at which mobs are able to steal items
	#Range: 0.0 ~ 1.7976931348623157E308
	"Difficulty Steal AI" = 0.0
	#Chance for mobs to be able to ride a guardian
	#Range: 0.0 ~ 1.0
	"Guardian Chance" = 1.0
	#Chance for mobs to be able to ride a parrot
	#Range: 0.0 ~ 1.0
	"Fly Chance" = 0.5

#Configs regarding mobs spawning with equipment
[equipment]
	#Blacklist for mods. Add modid to prevent items from that mod being equipped. (For individual items use the equipment.json)
	"Item Blacklist" = []
	#Use blacklist as whitelist
	"Item Whitelist" = false
	#Blacklist for items mobs should never be able to use.
	#Use as in using the item similar to players (e.g. shooting bows)
	"Item Use Blacklist" = ["bigbrain:buckler"]
	#Turn the use blacklist into a whitelist
	"Item Use Whitelist" = false
	#Blacklist for specific mobs and items they shouldnt use (e.g. skeletons already use bows)
	#<entity registry name-item>
	#For different items but same entity use multiple lines
	#Some special names are BOW, TRIDEN, CROSSBOW refering to every bow/trident/crossbow item (So you dont need to type e.g. every bow item)
	"Entity Item Use Blacklist" = ["minecraft:drowned;TRIDENT", "minecraft:illusioner;BOW", "minecraft:piglin;CROSSBOW", "minecraft:pillager;CROSSBOW", "minecraft:skeleton;BOW", "minecraft:snow_golem;minecraft:snowball", "minecraft:stray;BOW", "minecraft:wither_skeleton;BOW"]
	#Base chance that a mob can have one piece of armor
	#Range: 0.0 ~ 1.0
	"Equipment Chance" = 0.1
	#Base chance for each additional armor pieces
	#Range: 0.0 ~ 1.0
	"Additional Equipment Chance" = 0.3
	#Adds additional x*difficulty% to base equip chance
	#Range: 0.0 ~ 1.7976931348623157E308
	"Equipment Addition" = 0.3
	#Chance for mobs to have a weapon
	#Range: 0.0 ~ 1.0
	"Weapon Chance" = 0.05
	#Adds additional x*difficulty% to base weapon chance
	#Range: 0.0 ~ 1.7976931348623157E308
	"Weapon Chance Add" = 0.3
	#Base chance for each armor pieces to get enchanted
	#Range: 0.0 ~ 1.0
	"Enchanting Chance" = 0.2
	#Adds additional x*difficulty% to base enchanting chance
	#Range: 0.0 ~ 1.7976931348623157E308
	"Enchanting Addition" = 0.2
	#Specify min and max enchanting levels according to difficulty. difficulty-minLevel-maxLevel
	"Enchanting Calc" = ["0-5-10", "25-5-15", "50-10-17", "100-15-25", "200-20-30", "250-30-35"]
	#Chance for mobs to have an item in offhand
	#Range: 0.0 ~ 1.0
	"Item Equip Chance" = 0.05
	#Adds additional x*difficulty% to base item chance
	#Range: 0.0 ~ 1.7976931348623157E308
	"Item Chance add" = 0.2
	#Should mobs drop the armor equipped through this mod? (Other methods e.g. through vanilla is not included)
	"Should drop equipment" = false

#Settings for attribute modifiers
[attributes]
	#Health will be multiplied by difficulty*0.016*x. Set to 0 to disable
	#Range: 0.0 ~ 1.7976931348623157E308
	"Health Increase Multiplier" = 1
	#Health will be multiplied by at maximum this. Set to 0 means no limit
	#Range: 0.0 ~ 1.7976931348623157E308
	"Max Health Increase" = 3.0
	#Round health to the nearest x. Set to 0 to disable
	#Range: 0.0 ~ 1.7976931348623157E308
	"Round HP" = 0.5
	#Damage will be multiplied by difficulty*0.008*x. Set to 0 to disable
	#Range: 0.0 ~ 1.7976931348623157E308
	"Damage Increase Multiplier" = 1.5
	#Damage will be multiplied by at maximum this. Set to 0 means no limit
	#Range: 0.0 ~ 1.7976931348623157E308
	"Max Damage Increase" = 3.0
	#Speed will be increased by difficulty*0.0008*x. Set to 0 to disable
	#Range: 0.0 ~ 1.7976931348623157E308
	"Speed Increase" = 1.5
	#Maximum increase in speed
	#Range: 0.0 ~ 1.0
	"Max Speed" = 0.133
	#Knockback will be increased by difficulty*0.002*x. Set to 0 to disable
	#Range: 0.0 ~ 1.7976931348623157E308
	"Knockback Increase" = 1.0
	#Maximum increase in knockback
	#Range: 0.0 ~ 1.0
	"Max Knockback" = 0.5
	#Magic resistance will be increased by difficulty*0.0016*x. Set to 0 to disable
	#Range: 0.0 ~ 1.7976931348623157E308
	"Magic Resistance Increase" = 1.0
	#Maximum increase in magic resistance. Magic reduction is percentage
	#Range: 0.0 ~ 1.0
	"Max Magic Resistance" = 0.2
	#Projectile Damage will be multiplied by 1+difficulty*0.008*x. Set to 0 to disable
	#Range: 0.0 ~ 1.7976931348623157E308
	"Projectile Damage Increase" = 1.0
	#Projectile damage will be multiplied by maximum of this
	#Range: 0.0 ~ 1.7976931348623157E308
	"Max Projectile Damage" = 2.0


```