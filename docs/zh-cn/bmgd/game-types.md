---
title: "游戏类型参考 (Game Types Reference)"
---

BMGD 支持 24 种游戏类型模板。每种都会向你的 GDD 添加特定类型的章节。

## 游戏类型

### 动作与战斗 (Action & Combat)

#### 动作平台 (Action Platformer)

带战斗机制的横向卷轴或 3D 平台跳跃。

**示例:** 空洞骑士 (Hollow Knight), 洛克人 (Mega Man), 蔚蓝 (Celeste)

**GDD 章节:**

- 移动系统 (跳跃, 冲刺, 墙壁机制)
- 战斗机制 (近战/远程, 连击)
- 关卡设计模式
- Boss 设计

#### 射击 (Shooter)

带瞄准机制的投射物战斗。

**示例:** 毁灭战士 (Doom), 使命召唤 (Call of Duty), 斯普拉遁 (Splatoon)

**GDD 章节:**

- 武器系统
- 瞄准与精度
- 敌人 AI 模式
- 关卡/竞技场设计
- 多人游戏考虑

#### 格斗 (Fighting)

带连击和帧数据的 1v1 战斗。

**示例:** 街头霸王 (Street Fighter), 铁拳 (Tekken), 任天堂明星大乱斗 (Super Smash Bros.)

**GDD 章节:**

- 帧数据系统
- 连击机制
- 角色招式表
- 竞技平衡
- 网络代码 (Netcode) 需求

### 策略与战术 (Strategy & Tactics)

#### 策略 (Strategy)

带战术决策的资源管理。

**示例:** 星际争霸 (StarCraft), 文明 (Civilization), 欧陆风云 (Europa Universalis)

**GDD 章节:**

- 资源系统
- 单位/建筑设计
- AI 对手行为
- 地图/剧本设计
- 胜利条件

#### 回合制战术 (Turn-Based Tactics)

带回合顺序的网格移动。

**示例:** XCOM, 火焰纹章 (Fire Emblem), 陷阵之志 (Into the Breach)

**GDD 章节:**

- 网格与移动系统
- 回合顺序机制
- 掩体与站位
- 单位进程
- 程序化任务生成

#### 塔防 (Tower Defense)

带塔放置的波次防御。

**示例:** 气球塔防 (Bloons TD), 皇家守卫军 (Kingdom Rush), 植物大战僵尸 (Plants vs. Zombies)

**GDD 章节:**

- 塔类型与升级
- 波次设计与节奏
- 经济系统
- 地图设计模式
- 元进程 (Meta-progression)

### RPG 与进程 (RPG & Progression)

#### RPG

带属性、库存和任务的角色进程。

**示例:** 最终幻想 (Final Fantasy), 巫师 (The Witcher), 博德之门 (Baldur's Gate)

**GDD 章节:**

- 角色属性与等级
- 库存与装备
- 任务系统设计
- 战斗系统 (动作/回合制)
- 技能树与构建 (Builds)

#### Roguelike

带永久死亡 (Permadeath) 和基于 Run 进程的程序化生成。

**示例:** 黑帝斯 (Hades), 删除细胞 (Dead Cells), 洞穴探险 (Spelunky)

**GDD 章节:**

- 程序化生成规则
- 永久死亡与持久性
- Run 结构与节奏
- 物品/能力协同 (Synergies)
- 元进程系统

#### 银河城 (Metroidvania)

带能力锁的互联世界。

**示例:** 银河战士 (Metroid), 恶魔城：月下夜想曲 (Castlevania: Symphony of the Night), 奥日 (Ori)

**GDD 章节:**

- 世界地图连通性
- 能力锁设计 (Ability gating)
- 回溯流程
- 秘密与收集品放置
- 强化进程

### 叙事与故事 (Narrative & Story)

#### 冒险 (Adventure)

带解谜元素的故事驱动探索。

**示例:** 猴岛小英雄 (Monkey Island), 神秘岛 (Myst), 奇异人生 (Life is Strange)

**GDD 章节:**

- 谜题设计
- 叙事传递
- 探索机制
- 对话系统
- 故事分支

#### 视觉小说 (Visual Novel)

带分支故事的叙事选择。

**示例:** 心跳文学部 (Doki Doki Literature Club), 逆转裁判 (Phoenix Wright), 命运石之门 (Steins;Gate)

**GDD 章节:**

- 分支叙事结构
- 选择与后果
- 角色路线
- UI/呈现
- 存档/读档状态

#### 基于文本 (Text-Based)

带解析器或选择机制的文本输入/输出游戏。

**示例:** Zork, 80 Days, 矮人要塞 (Dwarf Fortress) (冒险模式)

**GDD 章节:**

- 解析器或选择系统
- 世界模型
- 叙事结构
- 文本呈现
- 存档状态管理

### 模拟与管理 (Simulation & Management)

#### 模拟 (Simulation)

带管理和建造的现实系统。

**示例:** 模拟城市 (SimCity), 过山车大亨 (RollerCoaster Tycoon), 模拟人生 (The Sims)

**GDD 章节:**

- 核心模拟循环
- 经济建模
- AI Agents/市民
- 建造/施工
- 失败状态

#### 沙盒 (Sandbox)

带建造和最小目标的创作自由。

**示例:** 我的世界 (Minecraft), 泰拉瑞亚 (Terraria), Garry's Mod

**GDD 章节:**

- 创作工具
- 物理/交互系统
- 持久性与保存
- 分享/社区功能
- 可选目标

### 体育与竞速 (Sports & Racing)

#### 竞速 (Racing)

带赛道和圈速的车辆控制。

**示例:** 马里奥赛车 (Mario Kart), 极限竞速 (Forza), 极品飞车 (Need for Speed)

**GDD 章节:**

- 车辆物理模型
- 赛道设计
- AI 对手
- 进程/生涯模式
- 多人竞速

#### 体育 (Sports)

基于团队或个人的体育模拟。

**示例:** FIFA, NBA 2K, 托尼·霍克职业滑板 (Tony Hawk's Pro Skater)

**GDD 章节:**

- 运动特定规则
- 球员/团队管理
- AI 对手行为
- 赛季/生涯模式
- 多人模式

### 多人游戏 (Multiplayer)

#### MOBA

带英雄选择的多人团队战斗。

**示例:** 英雄联盟 (League of Legends), Dota 2, 神之浩劫 (Smite)

**GDD 章节:**

- 英雄/冠军设计
- 分路与地图设计
- 团队组成
- 匹配 (Matchmaking)
- 经济 (金币/物品)

#### 派对游戏 (Party Game)

带小游戏的本地多人游戏。

**示例:** 马里奥派对 (Mario Party), Jackbox, 分手厨房 (Overcooked)

**GDD 章节:**

- 小游戏设计模式
- 控制器支持
- 回合/游戏结构
- 计分系统
- 玩家数量灵活性

### 恐怖与生存 (Horror & Survival)

#### 生存 (Survival)

带制作和持续威胁的资源收集。

**示例:** 饥荒 (Don't Starve), 一起玩农场 (Subnautica), 森林 (The Forest)

**GDD 章节:**

- 资源收集
- 制作系统
- 饥饿/生命/需求
- 威胁系统
- 基地建设

#### 恐怖 (Horror)

资源有限的氛围和张力。

**示例:** 生化危机 (Resident Evil), 寂静岭 (Silent Hill), 失忆症 (Amnesia)

**GDD 章节:**

- 恐惧机制
- 资源稀缺
- 音效设计
- 光照与可见性
- 敌人/威胁设计

### 休闲与进程 (Casual & Progression)

#### 解谜 (Puzzle)

基于逻辑的挑战和问题解决。

**示例:** 俄罗斯方块 (Tetris), 传送门 (Portal), 见证者 (The Witness)

**GDD 章节:**

- 谜题机制
- 难度进程
- 提示系统
- 关卡结构
- 评分/评级

#### 放置/增量 (Idle/Incremental)

带升级和自动化的被动进程。

**示例:** 饼干点击器 (Cookie Clicker), 冒险资本家 (Adventure Capitalist), 点击英雄 (Clicker Heroes)

**GDD 章节:**

- 核心循环设计
- 声望 (Prestige) 系统
- 自动化解锁
- 数值数值缩放 (Number scaling)
- 离线进度

#### 卡牌游戏 (Card Game)

带卡牌机制的牌组构建。

**示例:** 杀戮尖塔 (Slay the Spire), 炉石传说 (Hearthstone), 万智牌竞技场 (Magic: The Gathering Arena)

**GDD 章节:**

- 卡牌设计框架
- 牌组构建规则
- 法力/资源系统
- 稀有度与收集
- 竞技平衡

### 节奏 (Rhythm)

#### 节奏 (Rhythm)

带基于时机的玩法音乐同步。

**示例:** 吉他英雄 (Guitar Hero), 节奏光剑 (Beat Saber), 节奏地牢 (Crypt of the NecroDancer)

**GDD 章节:**

- 音符/节拍映射
- 计分系统
- 难度级别
- 音乐许可
- 输入方法

## 混合类型

可以组合多种游戏类型。将包含所有选定类型的 GDD 章节。

| 混合 | 组件 | 组合章节 |
|--------|------------|-------------------|
| Action RPG | Action Platformer + RPG | 移动, 战斗, 属性, 库存 |
| Survival Horror | Survival + Horror | 资源, 制作, 氛围, 恐惧 |
| Roguelike Deckbuilder | Roguelike + Card Game | Run 结构, 程序化生成, 卡牌 |
| Tactical RPG | Turn-Based Tactics + RPG | 网格移动, 属性, 进程 |
| Open World Survival | Sandbox + Survival | 建造, 制作, 探索 |
