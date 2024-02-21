---
title: 👋 Getting Started
sidebar_position: 1
description: This tutorial helps you get started with NotQuests from zero to hero - with an easy-to-follow, practical example
keywords: [notquests, tutorial, getting started, beginner, guide]
---

:::danger Before you read

本指南是根据 **5.17.1 或更高版本** 和 **[paper 1.20.1](https://papermc.io/)** 设计的。

旧版本或 Spigot 服务器将具有较少的功能和不同的命令。
如果您使用的是旧版本或 Spigot，请自行研究，因为命令会有所不同。

:::

:::info Incomplete docs

我知道这里的文档非常不完整，只涵盖了 notquests 实际功能的 10%。 由于文档是开源的，这不是我的错，而是你的错，因为你，或者更确切地说，社区，很懒！ **你太无耻了！**

一旦您了解了有关 notquests 的更多信息，您就可以成为我们的一员**[在此处为我们的文档做出贡献](https://github.com/AlessioGr/NotQuests-Docs/tree/main/docs)**（需要 GitHub 帐户， 但可以在那里编辑文档） - 欢迎任何贡献！ ❤️

:::

让我们来探索**NotQuests！** 有两种方法可以开始：

- 要么继续阅读本指南
- 或者观看我们的 [youtube视频教程](https://www.youtube.com/watch?v=OC45_H3Tv8Y)。请注意，视频教程是使用 NotQuests v3 制作的，某些命令可能略有不同。

## 结构

NotQuests 中的任务可以有不同的属性，例如：

- **displayName**: 玩家实际看到的任务名称
- **description**: 任务描述
- **limits**: 玩家可以接受、完成或失败任务的最大次数
- *还有更多...*

此外，我们还可以将以下内容附加到任务中：

- **Objectives**: 目标基本上是“玩家需要做的事情”。 一旦任务的所有目标都完成，任务本身就完成了。
- **Requirements**: 这些决定了玩家是否可以接受任务。 如果玩家未满足所有要求，则无法开始任务。 在内部，它们被称为“条件”。
- **Rewards**: 不言自明！奖励是玩家完成任务后将 "执行 "的操作。
- **Triggers**: 触发器的理解比较复杂。基本上，一旦有*事情发生*，触发器就会 "执行 "一个动作。

## 命令

有两种类型的命令：

- `/q` 或 `/notquests` 用于**玩家命令**。所有玩家都可以使用此命令。
- `/qa` 或 `/notquestsadmin` 用于 **管理命令**。 我们将用它来制作和编辑我们的任务！

在 NotQuests 中，我们使用命令创建所有任务。 无需编辑复杂的配置文件！

### Command Completions
> 由于图片无法汉化，所以你看到的图片都是英文版本  
该提示只会出现一次

你所写的每一个用空格隔开的内容都称为*参数*。在下面的图片中，**edit** 和 **questname** 是两个参数：

![Command Completions](/img/getting-started/command-completions.png)

如果您在最后一个参数后按空格键，我们的智能命令系统将向您显示“下一个”参数是什么。 如果您遇到命令问题，只需确保最后一个字符是空格并**阅读命令补全**！

:::tip 仍然卡住？

如果命令完成还不够，并且您仍然不知道命令是如何工作的，只需**按 Enter** 并运行命令！ 它会向您显示**帮助菜单**。 只要阅读它，它就会告诉您它需要什么参数以及它们的作用。

:::

## 创建第一个任务

我认为最好、最简单的学习方法就是边做边学！ 因此，让我们不要在无聊的文档上浪费时间并创建我们的第一个任务：

`/qa create TheVirus`

然后它应该向您显示以下消息：

![Quest successfully created](/img/getting-started/quest-successfully-created.png)

### 1. 任务描述和显示名称

现在，初始任务名称不能有任何空格。它只是任务的标识符。不过，我们可以给它一个可以有空格的显示名称，这就是玩家实际看到的名称！

`/qa edit TheVirus displayName set 致命 病毒`

接下来，我们要为任务添加描述，该描述将显示在多个位置，例如，如果玩家尝试预览或接受任务：

`/qa edit TheVirus description set 一种致命的病毒感染了临冬城的居民。您必须杀死受感染的村民，防止病毒进一步扩散。`

现在，您的玩家在接受任务后会看到精美的描述和显示名称：

![After they accepted the Quest](/img/getting-started/after-accepting-with-description.png)

### 2. 要求

没有任何要求，每个玩家都能接受你的任务。不过，我们要做的任务会相当棘手！让我们要求玩家至少拥有 10 点任务点数，然后才能接受任务：

`/qa edit TheVirus requirements add QuestPoints moreOrEqualThan 10`

任务点数可以通过完成任务来获得，也可以手动分配。

如果玩家尝试接受任务但未满足要求，他们现在会看到以下内容。

![After they accepted the Quest](/img/getting-started/requirements-not-fulfilled.png)

为了让我们能够测试我们自己的任务，给自己 10 个任务点：

`/qa questpoints putyourminecraftnamehere add 10`

:::tip 感谢您的关注

如果您喜欢 NotQuests，请[**在 modrinth 上关注 NotQuests**](https://modrinth.com/plugin/notquests/versions) 😊 这将激励我为您带来更多更新和功能！
:::

### 3. Objectives

目标是每个任务的核心。 让我们添加第一个！

首先，玩家必须清除道路上受感染的僵尸制造的所有粪便：

`/qa edit TheVirus objectives add BreakBlocks dirt 64`

一旦玩家打破 64 个泥土，这个目标就会完成👍如果你愿意，你可以在那里指定多种材料。 例如，如果玩家可以破坏泥土或石头，则只需在那里输入“dirt,stone”即可。

现在，让我们为该目标添加一个描述：

`/qa edit TheVirus objectives edit 1 description set 受感染的僵尸在街上拉屎,打破 64 个污垢块即可将其清理干净！`

还有一个名字:

`/qa edit TheVirus objectives edit 1 displayName set Stinky Street`

让我们使用 `/q take TheVirus` 接受任务：

![After they accepted the Quest with first Objective](/img/getting-started/after-accepting-with-first-objective.png)

那很容易，不是吗？

#### Second Objective

我们继续下一个目标！街道已经清空！玩家现在应该杀死所有感染的村民：

`/qa edit TheVirus objectives add KillMobs zombie_villager 15`

在杀死15名僵尸村民之后，该目标将完成！现在让我们添加一个目标描述和名称：

`/qa edit TheVirus objectives edit 2 description set 你可以看到前面的感染村民！杀死他们全部，阻止病毒传播！`

`/qa edit TheVirus objectives edit 2 displayName set Zombies ahead!`

#### 目标依赖关系

现在，在接受这个任务后，您将会看到这个界面：

![After they accepted the Quest with second Objective](/img/getting-started/after-accepting-with-second-objective.png)

如您所见，两个目标都可见。您也可以按任意顺序完成它们。

然而，我们希望第二个目标"前方有僵尸！"只有在完成第一个目标后才可见和可完成。

为了实现这一点，我们需要向第二个目标添加一个条件，使玩家需要先完成第一个目标。在NotQuests中，有两种方法可以实现这一点（请选择其中一种）：

- **Easy way**: `/qa edit TheVirus objectives predefinedProgressOrder set firstToLast`. This also automatically sets the correct, same order for any future objectives you may add to this quest.
- **Harder way**: `/qa edit TheVirus objectives edit 2 conditions unlock add CompletedObjective 1`. You'd need to set this for every single objective of that quest. However, this way may give you more flexibility.

Done! If we take the Quest now, the second objective is hidden:

![After they accepted the Quest with second Objective which has a dependency](/img/getting-started/after-accepting-with-second-objective-and-dependency.png)

It will be unlocked once you complete the first objective 😀

### 4. Triggers

With Triggers, we can add some action to the Quest!

When the user reaches the second objective and has to kill the Zombie Villagers, he will notice one thing: **There are no Zombie Villagers to kill**. Why would they?

Let's make NotQuests **spawn some Zombie Villagers for him once he reaches the second objective**.

First, we need to create the action which spawns the zombie villagers. Actions can be created outside of Quests and re-used for every quest. Let's make a SpawnMob Action:

`/qa actions add Spawn15ZombieVillagers SpawnMob zombie_villager 15 PlayerLocation`

This action spawns 15 zombie villagers at the location wherever the player taking this Quest currently is 😄

Now, let's add the **trigger with this action** to our Quest:

`/qa edit TheVirus triggers add Spawn15ZombieVillagers BEGIN --applyon O2 --world_name ALL`

This runs the action "*Spawn15ZombieVillagers*" once we BEGIN O2 (objective 2) in ALL worlds (not limited to any world). Feel free to test it out — it will work 👍

![When you complete the first objective, zombie villagers will spawn](/img/getting-started/trigger-after-completing-first-objective.png)

### 5. Rewards

Your players will murder you if they waste their time on this super hard Quest without receiving any rewards. So let's add some:

- +2 Quest Points: `/qa edit TheVirus rewards add QuestPoints add 2`
- 2 Swords: `/qa edit TheVirus rewards add GiveItem hand 2`
  - For this reward, you have to hold the item in your hand while running that command. Otherwise, you can also run `/qa edit TheVirus rewards add GiveItem wooden_sword 2`
- +300 Money (if you have Vault installed): `/qa edit TheVirus rewards add Money add 300`
- Want to give a reward from some other plugin via commands? You can use the {PLAYER} placeholder there. Example: `/qa edit TheVirus rewards add ConsoleCommand cr give to {PLAYER} DailyCrate 2`

#### Reward Display Names

Once you complete the Quest, you will receive the rewards, but the player won't notice. That's because rewards are hidden (can be changed in the config) by default **unless you give them a display name**! So let's do that:

1. `/qa edit TheVirus rewards edit 1 displayName set +2 Quest Points`
2. `/qa edit TheVirus rewards edit 2 displayName set +2 handcrafted Wooden Swords`
3. `/qa edit TheVirus rewards edit 3 displayName set +300 Coins`

Done! Once you finish the Quest, you will see the rewards:

![Rewards are shown after you complete the Quest](/img/getting-started/quest-completed-rewards.png)

### 6. More Quest Settings

We don't want the player to take this Quest over and over and over and over again after they completed it. Let's limit that.

First, let's make it, so they can only accept it only when it has not been completed less than 20 hours ago:

`/qa edit TheVirus acceptCooldown complete set 20h`

20h = 20 hours. Now, let's give it a hard limit of 10 Quest completions. After 10 completions, the player cannot accept the Quest anymore, no matter how long they wait:

`/qa edit TheVirus limits completions 10`

Wanna make it so they cannot accept the quest if they have failed or aborted it 3 times or more? Easy:

`/qa edit TheVirus limits fails 3`

Alternatively, you could also prevent them from aborting the quest in the first place:

`/qa edit TheVirus abortEnabled false`

At last, let's set takeEnabled to false:

`/qa edit TheVirus takeEnabled false`

This will make it, so the player cannot take the Quest using the `/q take TheVirus` command. Instead, they have to take it by either right-clicking a Quest Giver NPC or a Quest Giver armor stand. More regarding that in the next section:

### 7. Taking the Quest

Use `/q take TheVirus` to take the Quest! You can also bind it to either Citizens NPCs or Armor stands using `/qa edit TheVirus npcs add [NPC ID]` or `/qa edit TheVirus armorstands add`.

The quest is saved in the `plugins/NotQuests/default/quests.yml` and `plugins/NotQuests/default/actions.yml` files.

## Advanced concepts

### Categories

You can group Quests together in categories. Categories are just a way to organize your Quests. Let's create a category called "Virus Quests":

`/qa categories create VirusQuests`

Now let's move our quest to that category (by default, it's in a category called "default").

`/qa edit TheVirus category set VirusQuests`

Done - that easy! Each Quest can only belong to one single category. Categories also determine the folder structure of NotQuests - and they'll even determine how it's displayed in the GUI!

#### Sub-categories

Each category can also have sub-categories. There can be unlimited sub-categories, and you can nest them how deep you want. Example of creating a category "Zombies" as a sub-category of "VirusQuests": `/qa categories create VirusQuests.Zombies`

#### Category display names

The name we specified above is also just the categorie's identifier. You can add a display name (which is what the player will actually see). It can contain spaces, or even color codes, just like quest names! Example:

`/qa categories edit VirusQuests displayName set <dark_green>Virus Quests <main>(dangerous)`

#### Category predefined progress order:

(todo, still need to write this up. Works like the predefined progress order for quests > objectives, but for category > quests. Super useful, this can make your life VERY easy and speed things up by a lot)

### Sub-Objectives

![Sub objectives](/img/getting-started/sub-objectives.png)

NotQuests supports sub-objectives! Each objective can have unlimited sub-objective. And each sub-objective can also have unlimited sub-sub-objectives.. and so on!

For that, there exists an "Objective" objective which is just meant as a holder for sub-objectives. In the screenshot, that would be "Improve soil quality".
Although any objective can have sub-objectives.

If you add sub-objectives to an "Objective" objective, it's completed once all its sub-objectives have been completed.
If you add sub-objectives to any other objective, you're only able to progress on it once all its sub-objectives have been completed.

**Example:**

1. `/qa edit quest objectives add Objective "<gold>Improve soil quality"`
2. `/qa edit quest objectives edit 1 objectives add BreakBlocks dirt 5`
3. `/qa edit quest objectives edit 1 objectives edit 1 displayName set Less dirt is good`
4. `/qa edit quest objectives edit 1 objectives add Jump 3.0 --taskDescription "Jump on the soil to make it better"`

### Objective condition types

Earlier in this tutorial, we've explained how you can add objective dependencies via conditions. The command was `/qa edit TheVirus objectives edit 2 conditions unlock add CompletedObjective`.

However, there are different kinds of conditions you can add to Objectives. This condition is an unclock condition, which determines if the objective is Hidden (= no progress is counted and you cannot complete it) or not.

However, you can ALSO add objective conditions which check if you can progress, or complete the objective. Should be super useful!

**Examples:**

- `/qa edit questname objectives edit 1 conditions unlock add Flying equals false` - Unlock condition. That's what you are used to. If you are flying, the objective remains locked / "Hidden"
- `/qa edit questname objectives edit 1 conditions progress add Flying equals false` - Objective is always shown, but if you are flying, you won't get any positive progress towards it
- `/qa edit questname objectives edit 1 conditions complete add Flying equals false` - Objective is always shown and you always get progress, but it won't complete if you don't fulfill the condition

### Variables as objectives

There are more possible objectives than you think there are. You can add any variable of notquests as an objective! An example would be if you wanted the objective to be "Play 100 minutes":

`/qa edit questname objectives add NumberVariable PlaytimeMinutes moreOrEqualThan 100`

What if the player already played for 100 minutes already, though? Let's make it, so the player has to play 100 MORE minutes - counting from the point of accepting the quest/unlocking the objective.

`/qa edit questname objectives add NumberVariable PlaytimeMinutes moreOrEqualThan PlaytimeMinutes+100`

This objective makes it so the player needs to play 100 MORE minutes. This is possible, as you are able to use expressions (math, other variables etc.) in many places in notquests (PlaytimeMinutes+100 is such an expression).

Imagine the possibilities! Dynamic objectives based on how much the player has already done / how strong they are / how much karma or questpoints they collected / how much they earned? An easy task with notquests!

### Advanced block/material selector

Anywhere you can specify blocks/materials (e.g. the BreakBlocks objective or the GiveItem action/reward), we use our block selector. You can not only specify one single block/material there, but multiple! Here's some examples:

`/qa edit questname objectives add BreakBlocks diamond_ore,deepslate_diamond_ore 20`

Yes! Finally you can make it so both kinds of diamond ore count towards the progress.

Or:

`/qa edit questname objectives add PlaceBlocks hand,acacia_log,spruce_log,birch_log,dark_oak_log 15`

You can see why that's super useful, right?

This even works in GiveItem actions, so you could give players multiple items at once!

### NotQuests expressions are actually really powerful!

NotQuests gives you the ability to make even more complex conditions much easier, if you want to. Boolean comparisons are now possible in expressions. Note: conditions can be used as quest requirements / objective conditions. They are the same.

Few examples of what's now possible:

- `/qa conditions add cname True equals (Money>10)&Flying`
  This checks if you are flying AND have more than $10
  - Another way to do this: `/qa conditions add cname True equals Condition(Conditions:Flying&IsRich)`
  - Or `/qa conditions add cname Condition equals Flying&IsRich`

You can also use | (or) operators or ! (negation) when using conditions in an expression.

Or:

`/qa conditions add moneyCondition Money moreThan 10+TagInteger(TagName:reputation)*TagInteger(TagName:level)`

This condition makes it so you need more than 10 + the value of the "reputation" tag multiplied by the value of the "level" tag money.

And now a very complex one:

`/qa actions add pp3 Money add ((TagInteger(TagName:points)>=4)*(10+30))+(!(TagInteger(TagName:points)>=4)*5)`

If your "points" (from the Integer tag) are bigger or equal 4, this action will give you 40$. Otherwise, it will give you 5$. If you want to learn more about the tag system, head to the [tag system guide](/docs/tutorials/creating-a-reputation-system-with-tags).

[Full list of operators](https://pastebin.com/raw/qZqQmL8x).

NotQuests expressions like these can be used in a lot of places - so powerful!

### Profiles

Every player with the permission node "notquests.user.profiles" can now create **profiles** in notquests! :fire:
Each profile has **their own quest points, tags active & completed quests etc.** This would allow players to start over if they want to, in order to choose a different path, do a speedrun or just to experience your RPG again - or whatever else!

Showing all your current profiles: `/notquests profiles show` (seen on the screenshot)
Creating a new profile: `/notquests profiles create profilename`
Changing your profile: `/notquests profiles change profilename`

## What next?

Now, start making Quests! On this website, you can find further information about NotQuests and help if you check out the [Documentation](/docs/documentation/docs/) tab on the top of this page. If you need any help, feel free to join our [Discord](https://discord.gg/7br638S5Ex).
